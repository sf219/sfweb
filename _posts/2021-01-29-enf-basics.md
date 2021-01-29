---
layout: post
title: "SPL2020-I: An invisible time-stamp"
description: "SPL2020-I: An invisible time-stamp"
comments: true
---
In this post, I aim to give a quick intro to the Electrical Network Frequency (ENF) and to provide a motivation to our letter on SPL.

<br/>

First of all, the ENF is the name of a forensic criterion used in digital videos or audio recordings. For simplicity, I'll focus on the video scenario. It has tons of applications, as [time of recording verification](https://aidfork.uvigo.es/solutions/vidinger/), [synchronization](https://terpconnect.umd.edu/~oard/pdf/icassp14.pdf), or [forgery detection](https://www.researchgate.net/profile/Yongjian_Hu/publication/262163750_Audio_Forgery_Detection_Based_on_Max_Offsets_for_Cross_Correlation_between_ENF_and_Reference_Signal/links/559b32cc08ae793d13822933.pdf), to name a few. But, how does it work?

<br/>

The electrical network has a nominal frequency of 50 Hz. That is, theoretically, it should be a beautiful waveform, as the following one:
<br />
<img align="middle" width="500" src="{{ site.url }}/images_post/SPL-I/temporal_perfect.png" alt="...">
<br />
<br />

Even though, due to the generating mechanisms of the electrical energy, when the power demand increases, the frequency decreases slightly (and conversely, when the power demand decreases, the frequency increases). In large scale networks, this leads to a random frequency drift, that can be considered unique in time. For instance, you may check the frequency in the European grid in real-time [here](https://www.swissgrid.ch/en/home/operation/grid-data/current-data.html#frequency).

<br/>

Finally, when using the voltage from the network to power lamps, the luminance they produce is proportional to the intensity they receive. Those skilled in the art would know there is a rectification process as well, but we shouldn't spoil a good story with non-linearities, should we?

<br/>

Hence, the variations in the frequency of the network translate to variations in the luminance of the lamps. And they can be captured with digital cameras. Don't believe me? Check this [Youtube video](https://youtu.be/u2g2YKe5Gcc). Or, for a realistic scenario, you can check this [one](https://www.youtube.com/watch?v=rCgGNPl9DmM). Do you see the blink in the background? That's the ENF.

<br/>

You may wonder why you don't see this variation with your own eyes. Well, it's simply too fast. Cameras are able to record it due to a SigProc phenomena called aliasing, that reduces significantly the frequency of the blink. But it's unreachable for the human eye.

<br/>

Then, all you have to do is to take the video, average the luminance of every pixel, and estimate the frequency (there are lots of methods with flashy names, as MUSIC or ESPRIT, for doing it). Then, comparing this frequency with a ground-truth (a reference signal you know that is right in advance) would allow you to obtain, for example, the time of recording. Remember, the frequency is unique in time: it would only match with the correct segment.

<br/>

Here you have an example. The red one is obtained directly from the Internet, while the blue one is obtained from a video recorded on real time.

<br />
<img align="middle" width="500" src="{{ site.url }}/images_post/SPL-I/enf.png" alt="...">
<br />
<br />

Everything seems pretty easy. Now, I can introduce one of the real problems. What if the ENF is not the only source of variation in the luminance of the video? What if, for instance, there is movement? Logically, most of the interesting videos in practice have movement. The method I depicted above fails under this scenario...

<br />
<img align="middle" width="500" src="{{ site.url }}/images_post/SPL-I/state_of_the_art.png" alt="...">
<br />
<br />

And this is the problem we tried to solve in our paper. As an spoiler, we obtained this:

<br />
<img align="middle" width="500" src="{{ site.url }}/images_post/SPL-I/completo.png" alt="...">
<br />
<br />

But I may write another entry only devoted to this. Hope you find this entertaining!
