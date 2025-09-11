# Power Sprout Assembly Guide, aZach_Release

The Power Sprout was designed to be a very inexpensive, flexible, eurorack power supply for a small rack or bench testing. It is good for someone’s first SMT project, but does not require SMT to work (other than shorting some pads). 

Highly inspired by/copied from Timo Rozendal’s USBpowerthingy and Winterbloom’s Micronova. Thanks for open sourcing your designs so I could learn and riff on them. I can only hope someone is inspired by this to make their own version.

![Assembled Power Sprout w/ no resistors, and shorted D1 and F1, to be used with USB-C connector with built in pull downs](/assets/images/Power_Sprout_crop.jpg)

# Supporting Documents

[Schematic](/Hardware/Schematic/Power%20Sprout%20Schematic.pdf)  
[BOM](/Hardware/BOM/BOM.CSV)

# Considerations Before Getting Started

## Input Voltage

The DD1718PA can boost anything from 3.3-11 volts to \+/-12 volts. It is important to consider the input voltage to decide how you should populate the board. In short:

* If using 5 volts   
  * short D1 (and possibly F1)  
  * If using USB-C consider if R1 and R2 are needed for CC1 and CC2 pulldowns  
* If using 9 volts or similar  
  * Install a schottkey or similar diode, 2+ amps.  
  * Cut the trace at where VCC connects to pins 11 and 12 on J1  
    

For more information, see the screen grabs below and keep reading.

![Diptrace](/assets/images/Screenshot%202025-09-08%20145948.png)
![Cut here if not using 5 Volt in](/assets/images/Screenshot%202025-09-08%20150059.png)

## Diode

If using usb/5 volts or similar, where there is low risk of reverse polarity, and a higher current (\~2+ amps), solder a jumper wire across the footprint D1. If using 9 volts, where reverse polarity power supplies are common, consider protecting the DD1718PA with a diode, preferably schottkey, but any diode with a high enough current will suffice. 

## Fuse

Footprint F1 is for a resettable polyfuse, and can be jumpered if using one isn’t desired. For USB implementations, jumpering from the input of D1 to the output of F1 is acceptable

## 5 Volt Out 

The Power Sprout presents the Voltage In at the 5 volt out of the eurorack connector. This is great if you’re using USB for the input, but less great if you pick 9 volts (as it will put 9 volts on your 5 volt bus and just ‘no’). There are two cut points under the DD1718PA to be used before soldering the module in place if you’re going to power it with anything other than 5 volts. 

## USB-C

USB-C is slightly less than universal. Footprints R1 and R2 are provided to pull the CC1 and CC2 lines to ground with a 5.1 kohm resistor in order signal to the usb source that the Power Sprout needs 5 volts to start negotiating power needs (sorta). Some USB-C connectors have internal pull down resistors already installed, in which case do not populate R1 and R2

Not all USB sources can supply the needed power, but many will. 

You could add a USB PD IC, which would allow the board to properly negotiate 9 volts, with fall back modes, but that’s a little beyond the scope of this guide. 

Finally, a USB-C to USB-A cable will almost always work, assuming the USB-A port can source the required power.
![R1, R2, F1, and D1](/assets/images/Screenshot%202025-09-08%20150158.png)

## Ask, Ask, Ask…

If anything doesn’t make sense, or you find yourself with questions, Ask\! There are tons of helpful folks online that would be happy to help. “There are dozens of us, Dozens\!” 

# Assembly Guide

After considering everything above, and making some decisions, get your workspace setup, any parts not included on hand, a little light refreshment, and start assembling\!

### Step 1\) 5 Volt out

Cut or not, depending on what you intend the input voltage to be, see picture

### Step 2\) SMT Assembly

Solder R1 and R2 (or don’t worry about it if you’re ok using USB-C to A cables)  
Solder or jump D1 and F1 depending on input voltage, see above. 

### Step 3\) Thru Hole Assembly

Solder the DD1718PA and pins.

Solder the input connector,DD1718PA, 16 pin output connector, and capacitors, in that order. Be mindful of each orientation (follow the orientation on the silk screen for the connectors, align the negative stripe of the capacitors with the white half of the footprint, and the DD1718PA should fit within its footprint). 

I like to solder the connectors while mated with their cable to act as a bit of a heat sink. Solder one or two pins, check the connector is flat and level with the board, and then solder the remaining pins. Trim capacitor leads and DD1718PA pins.

![][image3]

### Step 4\) Visual inspection

Give it a once over, appreciate your work, clean up any dry joints or stray solder or scuzzy flux.

### Step 5\) Test Before Using\!

If you’re going to be doing this kinda stuff, it’s imperative you use a multimeter to test that everything is working as expected, but you already knew that. It’s much better to let the smoke out of an inexpensive power supply than damage a module, so just test the thing before you actually start using it. This means powering it up and measuring the voltage at the output, on the \+12, \-12, and 5 volt rails. 

### Step 6\) Troubleshooting

I don’t know what could have gone wrong.   
Double check your solder joints,   
inspect for shorts, and   
reach out as needed. 

### Step 7\) Jamming Out

It’s Go Time\! 

Enjoy your tiny power supply in your new hyper focused rack. Consider making it a mounting plate (hole dimensions are on the back of the pcb, m2.5 screws, or similar), 3d print an existing design, or just hot glue the thing in place. 
