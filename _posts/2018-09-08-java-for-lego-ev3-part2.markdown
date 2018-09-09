---
layout: post
title:  "Java for LEGO EV3 (Part2 - Sound)"
date:   2018-09-08 15:38:00 -0400
author: Yingjie Song
categories: COMP2801
tag: 2801
---
<h2>2 Sound Output</h2>

EV3 has 4 types of sound output: &#x2780;play preset sound, like "beep"; &#x2781;play a note; &#x2782;play a tone &#x2783;play a wav file.

<h3>2.1 Sound class</h3>

Usage:

{% highlight java %}
import lejos.hardware.Sound;
{% endhighlight %}

<h4>2.1.1 Fileds</h4>

<table>
	<tr>
		<th>Type</th>
		<th><a href="http://www.lejos.org/ev3/docs/lejos/hardware/Sound.html#field.summary">Field</a></th>
	</tr>
	<tr>
		<td>int</td>
		<td>C2</td>
	</tr>
	<tr>
		<td>int[]</td>
		<td>FLUTE</td>
	</tr>
	<tr>
		<td>int[]</td>
		<td>PIANO</td>
	</tr>
	<tr>
		<td>int</td>
		<td>VOL_MAX</td>
	</tr>
	<tr>
		<td>String</td>
		<td>VOL_SETTING</td>
	</tr>
	<tr>
		<td>int[]</td>
		<td>XYLOPHONE</td>
	</tr>
</table>

<h4>2.1.2 Methods</h4>

[`beep()`][sound-beep]

[`playNote(int[] inst, int freq, int len)`][sound-playnote]

{% highlight java %}
// instrument:PIANO, frequency:1000Hz, length:5s
Sound.playNote(Sound.PIANO, 1000, 5000);
{% endhighlight %}

[`playTone(int aFrequency, int aDuration, int aVolume)`][sound-playtone]

{% highlight java %}
// frequency:C2, duration:2s, volume:50%
Sound.playTone(Sound.C2, 2000, 50);
{% endhighlight %}

[`playSample(File file, int vol)`][sound-playsample]

Check out the [Sound (leJOS EV3 API)][lejos-api-sound] for more info of the `Sound` class.

[lejos-api-sound]: http://www.lejos.org/ev3/docs/lejos/hardware/Sound.html

[sound-beep]: http://www.lejos.org/ev3/docs/lejos/hardware/Sound.html#beep--

[sound-playnote]: http://www.lejos.org/ev3/docs/lejos/hardware/Sound.html#playNote-int:A-int-int-

[sound-playtone]: http://www.lejos.org/ev3/docs/lejos/hardware/Sound.html#playTone-int-int-int-

[sound-playsample]: http://www.lejos.org/ev3/docs/lejos/hardware/Sound.html#playSample-java.io.File-int-

<h4>Note-to-Frequency chart</h4>

In case you need it.

<table>
	<tr>
		<th>Sound</th>
		<th>1</th>
		<th>2</th>
		<th>3</th>
		<th>4</th>
		<th>5</th>
		<th>6</th>
		<th>7</th>
		<th>8</th>
	</tr>
	<tr>
		<td>G&#x266F;</td>
		<td>52</td>
		<td>104</td>
		<td>208</td>
		<td>415</td>
		<td>831</td>
		<td>1661</td>
		<td>3322</td>
		<td></td>
	</tr>
	<tr>
		<td>G</td>
		<td>49</td>
		<td>98</td>
		<td>196</td>
		<td>392</td>
		<td>784</td>
		<td>1568</td>
		<td>3136</td>
		<td></td>
	</tr>
	<tr>
		<td>F&#x266F;</td>
		<td>46</td>
		<td>92</td>
		<td>185</td>
		<td>370</td>
		<td>740</td>
		<td>1480</td>
		<td>2960</td>
		<td></td>
	</tr>
	<tr>
		<td>F</td>
		<td>44</td>
		<td>87</td>
		<td>175</td>
		<td>349</td>
		<td>698</td>
		<td>1397</td>
		<td>2894</td>
		<td></td>
	</tr>
	<tr>
		<td>E</td>
		<td>41</td>
		<td>82</td>
		<td>165</td>
		<td>330</td>
		<td>659</td>
		<td>1319</td>
		<td>2637</td>
		<td></td>
	</tr>
	<tr>
		<td>D&#x266F;</td>
		<td>39</td>
		<td>78</td>
		<td>156</td>
		<td>311</td>
		<td>622</td>
		<td>1245</td>
		<td>2489</td>
		<td></td>
	</tr>
	<tr>
		<td>D</td>
		<td>37</td>
		<td>73</td>
		<td>147</td>
		<td>294</td>
		<td>587</td>
		<td>1175</td>
		<td>2349</td>
		<td></td>
	</tr>
	<tr>
		<td>C&#x266F;</td>
		<td>35</td>
		<td>69</td>
		<td>129</td>
		<td>277</td>
		<td>554</td>
		<td>1109</td>
		<td>2217</td>
		<td></td>
	</tr>
	<tr>
		<td>C</td>
		<td>33</td>
		<td>65</td>
		<td>131</td>
		<td>262</td>
		<td>523</td>
		<td>1047</td>
		<td>2093</td>
		<td>4186</td>
	</tr>
	<tr>
		<td>B</td>
		<td>31</td>
		<td>62</td>
		<td>123</td>
		<td>247</td>
		<td>494</td>
		<td>988</td>
		<td>1976</td>
		<td>3951</td>
	</tr>
	<tr>
		<td>A&#x266F;</td>
		<td>29</td>
		<td>58</td>
		<td>117</td>
		<td>233</td>
		<td>466</td>
		<td>932</td>
		<td>1865</td>
		<td>3729</td>
	</tr>
	<tr>
		<td>A</td>
		<td>28</td>
		<td>55</td>
		<td>110</td>
		<td>220</td>
		<td>440</td>
		<td>880</td>
		<td>1760</td>
		<td>3520</td>
	</tr>
</table>