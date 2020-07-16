---
layout: post
title: ESP8266 Firmware extraction & MQTT Transfer Protocol sniffing!
---



![_config.yml]({{ site.baseurl }}/images/20200413_040046.jpg)

This post is about my recent work with an IOT company. Our project was about IOT Security Intrusion/Anomaly Detection program. 
Initially we started with an IOT device which sends temperature readings over WIFI to a secured server. The protocol we used was an unsecured  MQTT broker and ESP8226 nodemcu chip.
First our task was sniffing temperature which was sent to our server,
Here's how I did it. Pretty simple 
