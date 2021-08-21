---
layout: post
title:  "Blinking an LED with Arduino using TinkerCAD"
date:   2020-09-09 10:18:14 +0800
categories: electronics
published: true
author: Harvey Labis Abiagador
---

<h1>Context</h1>

<h1>Video Link</h1>
[![Blinking an LED with Arduino using TinkerCAD](https://img.youtube.com/vi/x_pJYZoRgmk/0.jpg)](https://youtu.be/x_pJYZoRgmk "Blinking an LED with Arduino using TinkerCAD")

<h1>Circuit Diagram</h1>

<h1>Code</h1>
Here's the code that I demonstrated in the video. To use this with TinkerCAD, simply 
{% highlight ruby %}

void setup(){
    pinMode(13, OUTPUT); #=> make the LED as output; light
}

void loop(){
    digitalWrite(13, HIGH); #=> HIGH - give 5 volts 
    delay(1000);    #=> wait for 1 sec = 1000 ms
    digitalWrite(13, LOW); #=> LOW - give 0 volts
    delay(1000);    #=> wait for 1 sec = 1000 ms
}

{% endhighlight %}


