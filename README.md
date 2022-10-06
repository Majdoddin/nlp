# Some experiments with Open AI's Whisper
## Pyannote plays and Whisper rhymes [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1qenfNUjd0nafSp9nRwS8DgBrsH6HAdD1#scrollTo=RQyROdrfsvk4)

OpenAI's [**Whisper**](https://openai.com/blog/whisper/) does a great job transcribing audio files, show how it "[beats it](https://colab.research.google.com/drive/1T5iOKDbyv9_8cCI1J0hSfOG3oBMX49Zx?usp=sharing)"!

Andrej Karpathy's [Lexicap](https://karpathy.ai/lexicap/index.html), uses Whisper to transcribe all Lex Friedman's podcasts.

Andrej [suggests](https://twitter.com/karpathy/status/1574476200801538048?s=20&t=s5IMMXOYjBI6-91dib6w8g) training a classifier on top of  Whisper model features to identify Lex, so we can visualize the speaker in the transcript. But, as [pointed out](https://twitter.com/tarantulae/status/1574493613362388992?s=20&t=s5IMMXOYjBI6-91dib6w8g) by Christian Perone, it seems that features from whisper wouldn't be that great for speaker recognition as its main objective is basically to ignore speaker differences.

In the following, I use [**`pyannote-audio`**](https://github.com/pyannote/pyannote-audio), a speaker diarization toolkit by Hervé Bredin, to identify the speakers, and then match it with the transcriptions of Whispr. I do it on the first 30 minutes of  Lex's 2nd [interview](https://youtu.be/SGzMElJ11Cc) with Yann LeCun. Run the notebook on Colab or check the resulting [**Webpage**](https://majdoddin.github.io/lexicap.html). 

The result is alright, albeit it is tricky to match the diarizations at the moments that the speaker changes, for example [this part](https://majdoddin.github.io/lexicap.html#00:03:09.520). 

I think we should come up with a clever way to combine the two NNs, to generate transcriptins with diarization.

## OpenAI's Whisper beats it! [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1T5iOKDbyv9_8cCI1J0hSfOG3oBMX49Zx)
Andrej [@karpathy](https://twitter.com/karpathy/status/1574474950416617472?s=20&t=fQkyC3t3qjG0WYZ-AAXMFw) downloaded all ~322 episodes of @lexfridman
 podcast and used OpenAI [Whisper](https://github.com/openai/whisper) to [transcribe](https://karpathy.ai/lexicap/index.html) them. People talk mostly clearly in a podcast, so I have a really TOUGH mission for Whisper: [Beat It](https://youtu.be/oRdxUFDoQe0) song of Michael Jackson. Michael sings fast and full of emotions, accompanied by a chorus, and with a really rough music. <br>

The result totally surpasses my expectations, fantastic!

It seems the model uses some randomness, and can behave strangely. For example, running it a [2nd time](#scrollTo=COmkiVmKNzrC&line=1&uniqifier=1), it almost ommits part 2 of verse 1 [01:05.000 --> 01:26.000]! 
