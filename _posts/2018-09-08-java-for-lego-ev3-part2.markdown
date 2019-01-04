---
layout: post
title:  "Java for LEGO EV3 (Part2 - Sound)"
date:   2018-09-08 15:38:00 -0400
author: Yingjie Song
categories: COMP2801
tag: 2801
---
## 2 Sound Output ##

EV3 has 4 types of sound output: &#x2780;play preset sound, like "beep"; &#x2781;play a note; &#x2782;play a tone &#x2783;play a wav file.

### 2.1 Sound class ###

Usage:

{% highlight java %}
import lejos.hardware.Sound;
{% endhighlight %}

#### 2.1.1 Fileds ####

Type|[Field](http://www.lejos.org/ev3/docs/lejos/hardware/Sound.html#field.summary)
--|--
int|C2
int|FLUTE
int|PIANO
int|VOL_MAX
int|VOL_SETTING
int|XYLOPHONE

#### 2.1.2 Methods ####

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

#### Note-to-Frequency chart ####

In case you need it.

Sound|1|2|3|4|5|6|7|8
--|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:
G&#x266F;|52|104|208|415|831|1661|3322|
G        |49|98|196|392|784|1568|3136|
F&#x266F;|46|92|185|370|740|1480|2960|
F        |44|87|175|349|698|1397|2894|
E        |41|82|165|330|659|1319|2637|
D&#x266F;|39|78|156|311|622|1245|2489|
D        |37|73|147|294|587|1175|2349|
C&#x266F;|35|69|129|277|554|1109|2217|
C        |33|65|131|262|523|1047|2093|4186
B        |31|62|123|247|494|988|1976|3951
A&#x266F;|29|58|117|233|466|932|1865|3729
A        |28|55|110|220|440|880|1760|3520