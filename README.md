*If you like my code, please*  [![donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/donate/?hosted_button_id=KMGB76UZS5SH8)
# Pyannote plays and Whisper rhymes [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1HuvcY4tkTHPDzcwyVH77LCh_m8tP-Qet?usp=sharing)

Andrej Karpathy [suggested](https://twitter.com/karpathy/status/1574476200801538048?s=20&t=s5IMMXOYjBI6-91dib6w8g) training a classifier on top of  [openai/whisper](https://github.com/openai/whisper) model features to identify the speaker, so we can visualize the speaker in the transcript. But, as [pointed out](https://twitter.com/tarantulae/status/1574493613362388992?s=20&t=s5IMMXOYjBI6-91dib6w8g) by Christian Perone, it seems that features from whisper wouldn't be that great for speaker recognition as its main objective is basically to ignore speaker differences.

In the following, I use [**`pyannote-audio`**](https://github.com/pyannote/pyannote-audio), a speaker diarization toolkit by Hervé Bredin, to identify the speakers, and then match it with the transcriptions of Whispr. I do it on the first 30 minutes of  Lex's 2nd [interview](https://youtu.be/SGzMElJ11Cc) with Yann LeCun. Check the result [**here**](https://majdoddin.github.io/lexicap.html). 

To make it easier to match the transcriptions to diarizations by speaker change, Sarah Kaiser [suggested](https://github.com/openai/whisper/discussions/264#discussioncomment-3825375) runnnig the pyannote.audio first and  then just running whisper on the split-by-speaker chunks. 
For sake of performance (and transcription quality?), we attach the audio segements into a single audio file with a silent spacer as a seperator, and run whisper on it. Enjoy it!
