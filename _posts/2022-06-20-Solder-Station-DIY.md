---
title: DIY A Solder Station 
description: Digital Solder Station Approach
author: HUYNGUYEN	
date: 2022-01-20 12:12:00 +0800
categories: [Blog]
tags: [Hobby, Blog, DIY]
pin: false
math: false
mermaid: false
image:
  path: /assets/posts/2024/POST-ID-7/ESP32-Attempting.png
  alt: Unknow PCB.
---

<!-- POST-ID-7 -->
## The needs of good solder stations without paying 1K+ USD
- I really need a micro-small soldering station with precise temperature control, which can prevent damage to electronic components due to prolonged exposure to high temperatures during soldering. From my previous experience soldering the 2SK170 Toshiba transistor, I found that heating it up to 350°C for 5 seconds can reduce its sensitivity.

## List of top solder station 2024

### Weller
- Weller WE1010: A high-end solder station with a digital temperature control and a wide temperature range. It also features a large LCD display and a variety of tips and accessories. ($300-$400)
- Weller WT1010: A high-end solder station with a digital temperature control and a wide temperature range. It also features a large LCD display and a variety of tips and accessories. ($400-$500)
...

### JBC
- JBC BT250: A high-end solder station with advanced features like temperature control, sleep mode, and calibration options. It also has a large LCD display and a ergonomic design. ($500-$600)
- JBC BT225 HF: A high-frequency solder station with a frequency range of 40-120 kHz and a temperature range of 150-450°C. ($400-$500)
- JBC BT220 HF: A high-frequency solder station with a frequency range of 40-120 kHz and a temperature range of 150-450°C. ($350-$450)
...

### Hakko
- Hakko FX-951 HF: A high-frequency solder station with a frequency range of 40-120 kHz and a temperature range of 150-450°C. ($350-$450)
- Hakko FX-951-66 HF: A high-frequency solder station with a frequency range of 40-120 kHz and a temperature range of 150-450°C. ($450-$550)
- Hakko FX-951: A high-performance solder station with a digital temperature control and a wide temperature range. It also features a large LCD display and a variety of tips and accessories. ($350-$450)
...

### 
- Ersa i-CON 1 HF: A high-frequency solder station with a frequency range of 40-120 kHz and a temperature range of 150-450°C. ($600-$700)
- Kurtz Ersa i-CON 2 HF: A high-frequency solder station with a frequency range of 40-120 kHz and a temperature range of 150-450°C. ($700-$800)

## Analog and digital solder stations - How's it works?
### Analog Solder Station
- Less accurate temperature control, typically ±5-10°C
- Manual calibration to ensure accurate temperature (using external tempture reader)
### Digital Solder Station
- The most critical concept of a Digital solder station that's using a casted heater with thermocouple and they having same Ground(GND). It's means when the heater works you cannot get the tempture of the cartridge
- Features like temperature lock, sleep mode, calibration, temperature profiles, timer, and alarm options

## Re-use of good cartridges from solder robot

## Solder station by Tempture controller PID (Omron 5ECC)

## Solder station by ESP32-S3 experiment

## Solder station by AVR MCUs

## High-Frequency Solder station by PWM Generator and Mosfet powered by high-speed driver (1hz-150Khz)

## Power source for heater by AC current

# Final

> To be continue..
{: .prompt-info }