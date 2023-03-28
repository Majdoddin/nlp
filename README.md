*If you like my code, please [donate!](./donation/donation.md)*
# Pyannote plays and Whisper rhymes [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Majdoddin/nlp/blob/main/Pyannote_plays_and_Whisper_rhymes_v_2_0.ipynb)

# Whisper's transcription plus Pyannote's Diarization 

**Update** - [@johnwyles](https://github.com/johnwyles) added HTML output for audio/video files from Google Drive, along with some fixes.

Using the new word-level timestamping of Whisper, the transcription words are highlighted as the video plays, with optional autoscroll. And the display on small displays is improved.

Moreover, the model is loaded just once, thus the whole thing runs much faster now. You can also hardcode your Huggingface token. 

---
Andrej Karpathy [suggested](https://twitter.com/karpathy/status/1574476200801538048?s=20&t=s5IMMXOYjBI6-91dib6w8g) training a classifier on top of  OpenAI [Whisper](https://openai.com/blog/whisper/) model features to identify the speaker, so we can visualize the speaker in the transcript. But, as [pointed out](https://twitter.com/tarantulae/status/1574493613362388992?s=20&t=s5IMMXOYjBI6-91dib6w8g) by Christian Perone, it seems that features from whisper wouldn't be that great for speaker recognition as its main objective is basically to ignore speaker differences.

In the following, I use [**`pyannote-audio`**](https://github.com/pyannote/pyannote-audio), a speaker diarization toolkit by Hervé Bredin, to identify the speakers, and then match it with the transcriptions of Whispr, linked to the video. The input can be YouTube or an video/audio file (also on Google Drive). I try it on a [Customer Support Call](https://youtu.be/hpZFJctBUHQ). Check the result [**here**](https://majdoddin.github.io/dyson.html).

To make it easier to match the transcriptions to diarizations by speaker change, Sarah Kaiser [suggested](https://github.com/openai/whisper/discussions/264#discussioncomment-3825375) runnnig the pyannote.audio first and  then just running whisper on the split-by-speaker chunks. 
For sake of performance (and transcription quality?), we attach the audio segements into a single audio file with a silent spacer as a seperator, and run whisper on it. Enjoy it!

(For sake of performance , I also tried attaching the audio segements into a single audio file with a silent -or beep- spacer as a seperator, and run whisper on it see it on [colab](https://colab.research.google.com/drive/1HuvcY4tkTHPDzcwyVH77LCh_m8tP-Qet?usp=sharing). It [works](https://majdoddin.github.io/lexicap.html) on some audio, and fails on some (Dyson's Interview). The problem is, whisper does not reliably make a timestap on a spacer. See the discussions [#139](https://github.com/openai/whisper/discussions/139) and [#29](https://github.com/openai/whisper/discussions/29))

The Markdown form used below is from [@ArthurFDLR](https://github.com/ArthurFDLR/whisper-youtube/).   

