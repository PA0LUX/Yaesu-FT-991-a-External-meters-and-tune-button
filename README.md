# Yaesu-FT-991-a-External-meters-and-tune-button
How to build an Arduino driven external meter display with a tune button for the Yaesu FT-991 (a)
Yaesu FT-991(a) external meter display and Tune button (By PA0LUX)

See also You Tube: https://youtu.be/XXXXXXXXX >>>>>to be uploaded

For details see the .docx

Probably this will also work for a FTdx-10, but I could not test that. The display should work but I cannot check is the scaling is correct.
This is a design of an Arduino (Nano) with a 2.8“ TFT with ILI9341 chip acting as a simultaneous (bargraph-)display of all 7 meters available in the FT-991(a). Also, a 3.2 “TFT with the same resolution (240 x 320) and ILI9341 chip will work fine. Touch is not used.

It reads all meter settings from the radio via CAT, through the Rs232 connector. 
The display will also show what power has been set in the radio. Besides that, it has a (momentary) pushbutton that can be used to tune the radio with 20 Watts (adjustable in .ino file).

The following data are displayed:

- SWR
- Comp
- IDD
- VDD
- ALC
- S Meter - is substituted by Power out when in TX.
- Power out - instead of S Meter, when in TX
 
- Present power setting
- Connection status

At tune button press, it stores the present power setting and the present mode. It will then engage an FM-N transmission. 
When released, the tuning signal will stop. The previous power and mode setting is restored after the button has been released. The tune power can be adapted in the sketch with the variable; set_tune_pwr "PC020;" The 020 means 20W. You can change it to anything between 005 and 100. 


The display shows a green “LED” to indicate that there is correct communication with the transceiver. The green led turns on when there is a correct answer received from the radio. It does check for correct baud rate. When not connected or when the transceiver is powered off (and 13,8 V still present), or a wrong baud rate, the green led will turn into a red one.

The circuit is to be connected to the RS232 connector of the transceiver (thru a null modem cable), thus leaving the USB connector of the transceiver available for other logging and/or CAT software.


