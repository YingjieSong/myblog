---
layout: post
title:  "Java for LEGO EV3 (Part1 - Display)"
date:   2018-09-02 17:52:00 -0400
categories: comp2801
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

The display resolution of EV3 is 178px &times; 128px, and the origin located at the left-top corner. When display by pixels, the ranges are 0~177 (x-axis) and 0~127 (y-axis). When display by columns and rows, the ranges are 0~16 (columns) and 0~7 (rows). Additionally, pixels are usually used to draw pictures while the columns and rows are usually used to display letters.

<table>
	<tr>
		<th>coordinate</th>
		<th>letter</th>
		<th>pixel</th>
	</tr>
	<tr>
		<td>x's range</td>
		<td>0~16</td>
		<td>0~177</td>
	</tr>
	<tr>
		<td>y's range</td>
		<td>0~7</td>
		<td>0~127</td>
	</tr>
</table>

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

<h4>1.2.1 Fields</h4>

<table>
	<tr>
		<th>Type</th>
		<th><a href="http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#field.summary">Field</a></th>
	</tr>
	<tr>
		<td>int</td>
		<td>CELL_HEIGHT</td>
	</tr>
	<tr>
		<td>int</td>
		<td>CELL_WIDTH</td>
	</tr>
	<tr>
		<td>int</td>
		<td>SCREEN_HEIGHT</td>
	</tr>
	<tr>
		<td>int</td>
		<td>SCREEN_WIDTH</td>
	</tr>
</table>

<h4>1.2.2 Methods</h4>

[`drawChar(char c, int x, int y)`][lcd-drawChar-char-int-int-]

{% highlight java %}
// output 'A' at (0, 0)
LCD.drawChar('A', 0, 0);
{% endhighlight %}

[`drawString(String str, int x, int y)`][lcd-drawString-java.lang.String-int-int-]

[`drawString(String str, int x, int y, boolean inverted)`][lcd-drawString-java.lang.String-int-int-boolean-]

[`drawInt(int i, int x, int y)`][lcd-drawInt-int-int-int-]

[`drawInt(int i, int places, int x, int y)`][lcd-drawInt-int-int-int-int-]

[`setPixel(int x, int y, int color)`][lcd-setPixel-int-int-int-]

[`getPixel(int x, int y)`][lcd-getPixel-int-int-]

[`clear()`][lcd-clear--]

[`clear(int y)`][lcd-clear-int-]

[`clear(int x, int y, int n)`][lcd-clear-int-int-int-]

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

[lcd-drawChar-char-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawChar-char-int-int-

[lcd-drawString-java.lang.String-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawString-java.lang.String-int-int-

[lcd-drawString-java.lang.String-int-int-boolean-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawString-java.lang.String-int-int-boolean-

[lcd-drawInt-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawInt-int-int-int-

[lcd-drawInt-int-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#drawInt-int-int-int-int-

[lcd-setPixel-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#setPixel-int-int-int-

[lcd-getPixel-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#getPixel-int-int-

[lcd-clear--]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#clear--

[lcd-clear-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#clear-int-

[lcd-clear-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#clear-int-int-int-

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

<h4>1.3.1 Fields</h4>

<table>
	<tr>
		<th>Type</th>
		<th><a href="http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#field.summary">Field</a></th>
	</tr>
	<tr>
		<td>int</td>
		<td>BASELINE</td>
	</tr>
	<tr>
		<td>int</td>
		<td>BLACK</td>
	</tr>
	<tr>
		<td>int</td>
		<td>BOTTOM</td>
	</tr>
	<tr>
		<td>int</td>
		<td>DOTTED</td>
	</tr>
	<tr>
		<td>int</td>
		<td>HCENTER</td>
	</tr>
	<tr>
		<td>int</td>
		<td>LEFT</td>
	</tr>
	<tr>
		<td>int</td>
		<td>RIGHT</td>
	</tr>
	<tr>
		<td>int</td>
		<td>SOLID</td>
	</tr>
	<tr>
		<td>int</td>
		<td>TOP</td>
	</tr>
	<tr>
		<td>int</td>
		<td>VCENTER</td>
	</tr>
	<tr>
		<td>int</td>
		<td>WHITE</td>
	</tr>
</table>

<h4>1.3.2 Methods</h4>

[`drawString(String str, int x, int y, int anchor)`][graphicslcd-drawString-java.lang.String-int-int-int-]

[`drawLine(int x0, int y0, int x1, int y1)`][graphicslcd-drawLine-int-int-int-int-]

[`drawRect(int x, int y, int width, int height)`][graphicslcd-drawRect-int-int-int-int-]

[`drawArc(int x, int y, int width, int height, int startAngle, int arcAngle)`][graphicslcd-drawArc-int-int-int-int-int-int-]

[`fillRect(int x, int y, int width, int height)`][graphicslcd-fillRect-int-int-int-int-]

[`fillArc(int x, int y, int width, int height, int startAngle, int arcAngle)`][graphicslcd-fillArc-int-int-int-int-int-int-]

[`getWidth()`][graphicslcd-getWidth--]

[`getHeight()`][graphicslcd-getHeight--]

[`setColor(int rgb)`][graphicslcd-setColor-int-]

[`setStrokeStyle(int style)`][graphicslcd-setStrokeStyle-int-]

[`drawImage(Image src, int x, int y, int anchor)`][graphicslcd-drawImage-lejos.hardware.lcd.Image-int-int-int-]

[`clear()`][graphicslcd-clear--]

Check out the [GraphicsLCD (leJOS EV3 API)][lejos-api-graphicslcd] for more info of the `GraphicsLCD` interface.

[lejos-api-graphicslcd]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html

[graphicslcd-drawString-java.lang.String-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#drawString-java.lang.String-int-int-int-

[graphicslcd-drawLine-int-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#drawLine-int-int-int-int-

[graphicslcd-drawRect-int-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#drawRect-int-int-int-int-

[graphicslcd-drawArc-int-int-int-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#drawArc-int-int-int-int-int-int-

[graphicslcd-fillRect-int-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#fillRect-int-int-int-int-

[graphicslcd-fillArc-int-int-int-int-int-int-]: http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#fillArc-int-int-int-int-int-int-

[graphicslcd-getWidth--]:http://www.lejos.org/ev3/docs/lejos/hardware/lcd/CommonLCD.html#getWidth--

[graphicslcd-getHeight--]:http://www.lejos.org/ev3/docs/lejos/hardware/lcd/CommonLCD.html#getHeight--

[graphicslcd-setColor-int-]:http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#setColor-int-

[graphicslcd-setStrokeStyle-int-]:http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#setStrokeStyle-int-

[graphicslcd-drawImage-lejos.hardware.lcd.Image-int-int-int-]:http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#drawImage-lejos.hardware.lcd.Image-int-int-int-

[graphicslcd-clear--]:http://www.lejos.org/ev3/docs/lejos/hardware/lcd/CommonLCD.html#clear--

