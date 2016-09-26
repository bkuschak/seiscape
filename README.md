# seiscape
Beaglebone cape with 24-bit sigma-delta A/D, VCXO, and split power supplies for a Yuma force-balance vertical seismometer

# Board mods
1. Substitute LT1761IS5-SD for U8 ADP7118, due to availability. Lift pin 4 and add 10.5K and 10K feedback divider for 2.5V output.   
2. Change R21 from 115K to 162K. Change R24 from 7.15K to 10K.   
3. Change R31 from 255K to 170K (162K). R26 from 15K to 10K.  
4. Change R23 from 100K to 17.7K to set +15V correctly.  
5. Change C6,C9,C12 to film caps.   
6. FIXME - add divider resistors to R2 and R4 to set +/-10V input span.   
7. Jumper JP16 to select P915 GPIO48 as CAPE_EN  
8. Add UBlox Neo-6M GPS receiver. 47 nH + 15 ohm bias-T, 1K+LED on PPS. Connected to UART4.  
9. Added LEDs on 3.3V power and LED[1:0]
10. FIXME - change ADR445ARMZ to ADR441ARMZ 2.5V ref, or ADR444ARMZ 4.096V ref. 5V is too close to AVDD span.  
11. Remove R9 and connect AD7175 CS# to PRU9_28/CS0

# Pin usage
    CS       <--> P9_28  PRU0_3 / CS0 (CS was tied low through resistor R9)  
    SCLK     <--> P9_31  PRU0_0 / SCK
    DIN      <--> P9_30  PRU0_2 / MOSI
    DOUT/RDY <--> P9_29  PRU0_1 / MISO  
    SYNC     <--> P9_27  PRU0_5 (not used by code yet)  
    CAPE_EN  <--> P9_15  GPIO_48
    PPS      <--> P8_7   TIMER4 and (not jumpered yet)
                  P9_16  PRU0_16 and
                  P8_16  EQEP2_INDEX
    VCXO     <--> P9_41  TCLKIN and (not jumpered yet)
                  P8_12  EQEP2A_IN
    LED0     <--> P8_12  PRU0_14
    LED1     <--> P8_11  PRU0_15
    
