---
layout: post
title:  "Java for LEGO Mindstorms EV3 (COMP2801)"
date:   2018-09-02 17:52:00 -0400
categories: jekyll update
---
<h2>Prerequisite</h2>

LeJOS, Eclipse, Java 7

([EV3 for Mac OS][ev3-mac-os])

([robot building instructions][building-instructions])

([LeJOS EV3 API][lejos-api])

[ev3-mac-os]: http://www.bartneck.de/2017/06/04/tutorial-on-how-to-install-and-run-java-on-lego-mindstorms-ev3-using-eclipse-on-mac-os-x/

[building-instructions]: https://education.lego.com/en-us/support/mindstorms-ev3/building-instructions#robot

[lejos-api]: http://www.lejos.org/ev3/docs/index.html

<h2>1 Screen Display</h2>

The display resolution of EV3 is 178px &times; 128px, and the origin is located at the left-top corner. When display by pixels, the ranges are 0~177 (x-axis) and 0~127 (y-axis). When display by columns and rows, the ranges are 0~16 (columns) and 0~7 (rows). Pixels are usually used to draw pictures while the columns and rows are usually used to display letters.

<h3>1.1 print methods</h3>

Regular `print` methods of Java.

{% highlight java %}
System.out.print();
System.out.println();
{% endhighlight %}

<h3>1.2 LCD class</h3>

Usage:

{% highlight java %}
import lejos.hardware.lcd.LCD;
{% endhighlight %}

<h4>1.2.1 basic attributes</h4>

<table>
	<tr>
		<th>data type</th>
		<th>attribute</th>
	</tr>
	<tr>
		<td>int</td>
		<td><a href="http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#CELL_HEIGHT">CELL_HEIGHT</a></td>
	</tr>
	<tr>
		<td>int</td>
		<td><a href="http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#CELL_WIDTH">CELL_WIDTH</a></td>
	</tr>
	<tr>
		<td>int</td>
		<td><a href="http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#SCREEN_HEIGHT">SCREEN_HEIGHT</a></td>
	</tr>
	<tr>
		<td>int</td>
		<td><a href="http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#SCREEN_WIDTH">SCREEN_WIDTH</a></td>
	</tr>
</table>

<h4>1.2.2 basic methods</h4>

[`drawChar(char c, int x, int y)`][drawChar-char-int-int-]

[`drawString(String str, int x, int y)`][drawString-java.lang.String-int-int-]

[`drawString(String str, int x, int y, boolean inverted)`][drawString-java.lang.String-int-int-boolean-]

[`drawInt(int i, int x, int y)`][drawInt-int-int-int-]

[`drawInt(int i, int places, int x, int y)`][drawInt-int-int-int-int-]

[`setPixel(int x, int y, int color)`][setPixel-int-int-int-]

[`getPixel(int x, int y)`][getPixel-int-int-]

[`clear()`][clear--]

[`clear(int y)`][clear-int-]

[`clear(int x, int y, int n)`][clear-int-int-int-]

All methods of `LCD` class are static methods, which can be called without creating an instance.

Example: 

{% highlight java %}
import lejos.hardware.lcd.LCD;
import lejos.utility.Delay;

public class HelloWorld {
	public static void main(String[] args) {
		for(int i=0; i<=7; i++) {
			LCD.drawString("HELLO WORLD", 0, i, i%2==1);
		}
		// wait for 5000 milliseconds
		Delay.msDelay(5000);
}
{% endhighlight %}

new method: [`msDelay(long period)`][ms-delay]

Check out the [LCD (leJOS EV3 API)][lejos-api-lcd] for more info of the `LCD` class.

[lejos-api-lcd]: http://www.lejos.org/ev3/docs/index.html?lejos/hardware/lcd/LCD.html

[drawChar-char-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawChar-char-int-int-

[drawString-java.lang.String-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawString-java.lang.String-int-int-

[drawString-java.lang.String-int-int-boolean-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawString-java.lang.String-int-int-boolean-

[drawInt-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawInt-int-int-int-

[drawInt-int-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawInt-int-int-int-int-

[setPixel-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#setPixel-int-int-int-

[getPixel-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#getPixel-int-int-

[clear--]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#clear--

[clear-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#clear-int-

[clear-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#clear-int-int-int-

[ms-delay]: http://www.lejos.org/ev3/docs/lejos/utility/Delay.html#msDelay-long-

<h3>1.3 GraphicsLCD interface</h3>

Usage:
{% highlight java %}
import lejos.hardware.BrickFinder;
import lejos.hardware.lcd.GraphicsLCD;

public class HelloWorld {
	public static void main(String[] args) {
		GraphicsLCD g = BrickFinder.getDefault().getGraphicsLCD();
	}
}
{% endhighlight %}

Check out the [GraphicsLCD (leJOS EV3 API)][lejos-api-graphics-lcd] for more info of the `GraphicsLCD` interface.

[lejos-api-graphics-lcd]: http://www.lejos.org/ev3/docs/index.html?lejos/hardware/lcd/GraphicsLCD.html