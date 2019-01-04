---
layout: post
title:  "Java for LEGO EV3 (Part1 - Display)"
date:   2018-09-02 17:52:00 -0400
author: Yingjie Song
categories: COMP2801
tag: 2801
---
## Prerequisite ##

LeJOS, Eclipse, Java 7

([Building Instructions][building-instructions])

([EV3 for Mac OS][ev3-mac-os])

([LeJOS EV3 API][lejos-api])

[ev3-mac-os]: http://www.bartneck.de/2017/06/04/tutorial-on-how-to-install-and-run-java-on-lego-mindstorms-ev3-using-eclipse-on-mac-os-x/

[building-instructions]: https://education.lego.com/en-us/support/mindstorms-ev3/building-instructions#robot

[lejos-api]: http://www.lejos.org/ev3/docs/index.html

## 1 Screen Display ##

The screen resolution of EV3 is 178px &times; 128px, and the origin located at the top left corner. When displayed in units of pixels, the value ranges are 0~177 (x-axis) and 0~127 (y-axis). When displayed in units of columns and rows, the value ranges are 0~16 (columns) and 0~7 (rows). Additionally, pixels are mostly used to draw graphics, while the columns and rows are mostly used to display texts.

Coordinate|Letter|Pixel
--|--|--
x's range|0~16|0~177
y's range|0~7|0~127

### 1.1 print methods ###

Regular `print` methods of Java.

{% highlight java %}
System.out.print();
System.out.println();
{% endhighlight %}

### 1.2 LCD class ###

Usage:

{% highlight java %}
import lejos.hardware.lcd.LCD;
{% endhighlight %}

#### 1.2.1 Fields ####

Type|[Field](http://www.lejos.org/ev3/docs/lejos/hardware/lcd/LCD.html#field.summary)
--|--
int|CELL_HEIGHT
int|CELL_WIDTH
int|SCREEN_HEIGHT
int|SCREEN_WIDTH

#### 1.2.2 Methods ####

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

### 1.3 GraphicsLCD interface ###

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

#### 1.3.1 Fields ####

Type|[Field](http://www.lejos.org/ev3/docs/lejos/hardware/lcd/GraphicsLCD.html#field.summary)
--|--
int|BASELINE
int|BLACK
int|BOTTOM
int|DOTTED
int|HCENTER
int|LEFT
int|RIGHT
int|SOLID
int|TOP
int|VCENTER
int|WHITE

#### 1.3.2 Methods ####

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

Example: draw a sine graph

{% highlight java%}
import lejos.hardware.BrickFinder;
import lejos.hardware.lcd.GraphicsLCD;

public class HelloWorld {
	public static void main(String[] args) {
		GraphicsLCD g = BrickFinder.getDefault().getGraphicsLCD();
		// the origin coordinates
		int xp=10;
		int yp=g.getHeight()/2;
		// draw x-axis
		g.drawLine(5, yp, 172, yp);
		// draw y-axis
		g.drawLine(xp, 5, xp, 122);
		// draw sine graph
		for(int i=-5; i<= 162; i++) {
			// each pixel represent 3°
			double si = Math.sin((3 * i) * Math.PI / 180);
			// calculate the value of y
			int yPoint=(int) (si * 30);
			// draw pixels
			LCD.setPixel(xp + i, yp - yPoint, 1);
		}
		// wait 5 seconds
		Delay.msDelay(5000);
	}
}
{% endhighlight %}

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