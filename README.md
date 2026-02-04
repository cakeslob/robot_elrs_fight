# robot_elrs_fight
robot fight electronics stuff

# Goals with this repo and board

- Read battery voltage from RM pocket controller 
- AM32 config over wifi (franks elrs fw)  https://github.com/frank26080115/ExpressLRS/tree/shrew-dev-am32v219
- Gyro support with MPU6050 (not for melty but for driving straigt) https://github.com/awigen/ExpressLRS/tree/add-rx-gyro-support
- Motor feedback from am32 with some kind of filter to drive straight or something, not sure how or what


This is, as am I,  not, a good guide. Franks guide is good, hes probably a pro.

https://github.com/frank26080115/Shrew-Dual-Brushed-ESC-with-ELRS/blob/master/docs/RM-XR2-PWM-Mod/readme.md

## WeAct ELRS board with frank firmware for AM32 config wifi

![](imgs/weact1.jpg)

I like the franks mod stuff, I like the ability to config AM32 drivers from phone.  I dont like the plastic antenna on the xr2. WeAct, the compoany who make the stm32f4 blackpill, released an ELRS reciver, with 6 io channels, and 1 battery VIN monitor pin. It sports an ESP32C3, so it can be used for AM32 config. It is priced pretty well(cheapest ESP32 elrs I have seen), and there is lots of room to solder. I forked franks shrew am32 branch and built for the weact board. Bench tests look promising, it works so far.


Size wise, its clearly bigger than the XR2 and RP2. It doesnt have a plastic antena, and it has an ESP32C3, and it has more IO and battery monitoring.

![](imgs/weact_xr.jpg)



# KNOWN ISSUES

There is something happening with Channel 1, aka GPIO2. When it enters AM32 config mode, with an ESC attatched, it forces a reset of the ESP32. I think it has something to do with whatever a strapon pin is. It works as a PWM pin though. I suggest just not using the pin, or using it as a servo pin. 