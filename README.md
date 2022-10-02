# esp32_audio_recording_SD
Using esp32 to record the audio and store in the SD card

# Citation
This reponsitory uses several Github links that two or three years old that already exist:
https://github.com/MhageGH/esp32_SoundRecorder
https://github.com/atomic14/esp32_sdcard_audio/tree/main/arduino-wav-sdcard

# Introduction
However, there are some bugs in these links. For example, the API parameters in the code were no longer applicable to the current version of Arduino 1.8.19.

This code shows how to record a WAV file to an SD card by using ESP32. The microphone is analog mic.

Hence,I have ried to solve all possible known problems, not only the SD card connection, but also the audio writing problem of our I2S. I hope you can make advantage of this.

## Contributors: 

Yongjie Yang - yoy28@pitt.edu 

# Details

## SD Card
Firstly, you should wiring the SD card to the esp32 and make sure the SD card should work well (there is a SD_test file in the examples Arduino).

![SD Card and its Breakout](https://github.com/lijinlunbeng/esp32_audio_recording_SD/blob/main/images/1.jpg)

The SD card and its breakout links is below:
https://www.amazon.com/dp/B08GYKNCCP?psc=1&ref=ppx_yo2ov_dt_b_product_details
https://www.amazon.com/dp/B07PFDFPPC?psc=1&ref=ppx_yo2ov_dt_b_product_details
https://www.amazon.com/dp/B08P517NW5?psc=1&ref=ppx_yo2ov_dt_b_product_details (Do not forget to buy a card reader)

The wiring is same as above links, IO5 - CS; IO23 - MOSI; 5V - VCC; IO19 - MISO; IO18- SCK; GND -GND. 

### problem
There is big problem maybe encountered: "Card Mount Failed";

To solve this problem:
1. SD module not wired properly 
2. Make sure your VCC is 5V, because some breakouts have LDO.
3. And make sure your SD card format is FAT32, if your card size over 64GB, please try to use like "DiskGenius" APP to change the card format.

## I2S code issue
Secondly, you should read the data from the ADC then using I2S write to the DAM in the esp32.

the wiring is same as above linkes, the output of microphone connects to the ESP32 IO35. (You can change to other else just change number of the variable ADC1_CHANNEL_7, ADC1_CHANNEL_7 is IO35).

### problem
The latest Arduino version has deleted some APIs ()

To solve this problem:
1. Pleaset read the official document. ![Official Document](https://github.com/lijinlunbeng/esp32_audio_recording_SD/blob/main/images/1.jpg)
2. I have already changed the code of APIs and their parameters in the code. 