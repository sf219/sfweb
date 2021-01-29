---
layout: post
title: "ENF: the not so invisible time-stamp"
description: "SPL2020-I"
comments: true
---
<head>
</head> 
<body>
<div align="justify">
<p>
In this post, I aim to give a quick intro to the Electrical Network Frequency (ENF) and to provide a motivation to our letter on SPL.
 </p>
 <br style="line-height:0px;" />

<p>
First of all, the ENF is the name of a forensic criterion used in digital videos or audio recordings. For simplicity, I'll focus on the video scenario. It has tons of applications, as <a href="https://aidfork.uvigo.es/solutions/vidinger/" target="_blanck">time of recording verification</a>, <a href="https://terpconnect.umd.edu/~oard/pdf/icassp14.pdf" target="_blanck">synchronization</a>, or <a href="https://www.researchgate.net/profile/Yongjian_Hu/publication/262163750_Audio_Forgery_Detection_Based_on_Max_Offsets_for_Cross_Correlation_between_ENF_and_Reference_Signal/links/559b32cc08ae793d13822933.pdf" target="_blanck">forgery detection</a>, to name a few. But, how does it work?
 </p>
<br style="line-height:0px;" />

<p>
The electrical network has a nominal frequency of 50 Hz. That is, theoretically, it should be a beautiful waveform, as the following one:
</p>
<br />
   <table width="100%" height="100%" align="center" valign="center">
   <tr><td>
<img src="{{ site.url }}/images_posts/SPL_I/temporal_perfect.png" class="center">
     </td></tr></table>
<br />
<br />
<p>
Even though, due to the generating mechanisms of the electrical energy, when the power demand increases, the frequency decreases slightly (and conversely, when the power demand decreases the frequency increases). In large scale networks, this leads to random frequency drift, that can be considered unique in time. For instance, you may check the frequency in the European grid in real-time <a href="https://www.swissgrid.ch/en/home/operation/grid-data/current-data.html#frequency" target="_blanck">here</a>.
</p>
<br style="line-height:0px;" />

<p>
Finally, when using the voltage from the network to power lamps, the luminance they produce is proportional to the intensity they receive. Those skilled in the art would say there's a rectification process as well, but we shouldn't spoil a good story with non-linearities, should we?
  </p>
  <br style="line-height:0px;" />
<p>
Hence, the variations in the frequency of the network translate to variations in the luminance of the lamps. And they can be captured with digital cameras. Don't believe me? Check this <a href="https://youtu.be/u2g2YKe5Gcc" target="_blanck">Youtube video</a>. Or, for a realistic scenario, you can check this <a href="https://www.youtube.com/watch?v=rCgGNPl9DmM" target="_blanck">one</a>. Do you see the blink in the background? That's the ENF.
  </p>
<br style="line-height:0px;" />

<p>
You may wonder why you don't see this variation with your own eyes. Well, it's simply too fast. Cameras can record it due to a SigProc phenomenon called aliasing, that reduces significantly the frequency of the blink. But it's unreachable for the human eye.
  </p>
  <br style="line-height:0px;" />
<p>
Then, comparing this frequency with a ground-truth (a reference signal you know in advance) allows us to obtain, for example, the time of recording. Remember, the frequency is unique in time: it would only match with the correct segment. Have a look at this example. The red one comes from the Internet, the blue one from a video recorded on real-time:
  </p>
<br />
   <table width="100%" height="100%" align="center" valign="center">
   <tr><td>
<img class="center" src="{{ site.url }}/images_posts/SPL_I/enf.png">
    </td></tr></table>
<br />
<br />
<p>
  Everything seems pretty easy. Now, I can introduce one of the real problems. What if the ENF is not the only source of variation in the luminance of the video? For instance, most of the interesting videos in practice have movement. The method I depicted above fails under this scenario (now, the blue one is the ground truth):
</p>
<br />
   <table width="100%" height="100%" align="center" valign="center">
   <tr><td>
<img class="center" src="{{ site.url }}/images_posts/SPL_I/state_of_the_art.png">
    </td></tr></table>
<br />
<br />
<p>
  And this is the problem we tried to solve in our paper. As a spoiler, we obtained:
</p>
   <table width="100%" height="100%" align="center" valign="center">
   <tr><td>
  <img class="center" src="{{ site.url }}/images_posts/SPL_I/completo.png">
    </td></tr></table>
<br />
<br />
<p>
  But I may write another entry only devoted to this. Hope you find the post entertaining!
</p>
</div>
</body>
