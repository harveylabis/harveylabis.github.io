---
layout: post
title:  "Driving a 7-segment display using Arduino UNO"
date:   2022-01-28 10:18:14 +0800
categories: electronics
published: true
author: Harvey Labis Abiagador

---

## Introduction
Supposedly, our laboratory assignment for our Digital Electronics class is driving a 7-Segment display. However, we weren't able to perform it due to time constraint brought by the Typhoon Odette. Curios as I am, I decided to perform it anyway without lab intruction from our instructor. My first attempt is to use an Arduino UNO to drive 7-segment display by mapping the corresponsing segments for a decimal digit and store it as an array.

![Circuit](/assets/sevenSegment/circuit_real.jpg)

**Video Demo:** [Driving a 7-segment display using Arduino UNO](https://www.youtube.com/watch?v=9R8G8nqu0_o)

## 7-Segment Displays
From the name itself, 7-segment display is just 7 LEDs arranged in a manner shown below.

![7-segment display](https://www.jameco.com/Jameco/workshop/TechTip/working-with-seven-segment-displays-fig1.jpg)

Each segment as a corresponding pin which to need to power on/off depending on the digit we want to display. For our purpose, we want to display digits 0 to 9.

## Components Used
- Arduino UNO 
- 7-Segment LED (5011AS)
- 7 x 220 Ohm resistors
- Jumper wires
- Breadboard

## Circuit Schematic 
![Circuit on Breadboard](/assets/sevenSegment/sevenSeg_arduino_fritzing_bb.png)

## Code
{% highlight c %}
/* 
 * Drive a 7-segment display 5011AS from 0 to 9
 * 
 * Author: Harvey Labis Abiagador
 * created: January 28, 2022
 */

int segments[7] =  {1, 2, 4, 6, 7, 9, 10};
const int segments_size = 7;

// mapping of decimals to corresponding segments
// 1 - HIGH or ON, 0 - LOW or OFF
const int zero[7] = {1, 1, 1, 1, 1, 1, 0};
const int one[7]  = {0, 0, 1, 1, 0, 0, 0};
const int two[7]  = {1, 1, 0, 1, 1, 0, 1};
const int three[7]= {0, 1, 1, 1, 1, 0, 1};
const int four[7] = {0, 0, 1, 1, 0, 1, 1};
const int five[7] = {0, 1, 1, 0, 1, 1, 1};
const int six[7]  = {1, 1, 1, 0, 1, 1, 1};
const int seven[7]= {0, 0, 1, 1, 1, 0, 0};
const int eight[7]= {1, 1, 1, 1, 1, 1, 1};
const int nine[7] = {0, 1, 1, 1, 1, 1, 1};
const int off[7]  = {0, 0, 0, 0, 0, 0, 0};


void setup() {
  for (int i = 0; i < segments_size; i++){
    pinMode(segments[i], OUTPUT);
    digitalWrite(segments[i], LOW);
    } 
}

void loop() {
  for (int c = 0; c < 10; c++){
    switch (c){
      case 0:
        light(zero);
        break;
      case 1:
        light(one);
        break;
      case 2:
        light(two);
        break;
      case 3:
        light(three);
        break;
      case 4:
        light(four);
        break;
      case 5:
        light(five);
         break;
      case 6:
        light(six);
        break;
      case 7:
        light(seven);
        break;
      case 8:
        light(eight);
        break;
      case 9:
        light(nine);
        break;
      default:
        light(off);
      }
    delay(1000);
  }
}

void light(int pinStatus[]){
  for (int p = 0; p < segments_size; p++){
    digitalWrite(segments[p], pinStatus[p]);
    }
}

{% endhighlight %}
