## 1. Why this has been done.
I compile the kernel at the WRT3200ACM, when compiling the kernel, the processor is very heavily loaded and the heat is high, the temperature on the processor has reached 100°C, which I think is not an acceptable value.I decided to install a cooling fan on the processor radiator in the chassis, as in the WRT1900AC v1 router model.
## 2. How to do this.
**Scheme**
The blue color (see schema) shows the elements that are located on the router board. The red color shows the items that you want to install on the router board. For a resistance +R and capacitor +C, there is no established seat on the board. You must attach these schematic elements to the board members that you have installed. The soldering of these elements is indicated in the diagram and photographs by red dots.
![image](https://github.com/ValCher1961/McDebian_WRT3200ACM/blob/master/hardware-mods/scheme.png)

**Photo**
The red dots on the schematic and the board show the soldering locations of the elements.
![image](https://github.com/ValCher1961/McDebian_WRT3200ACM/blob/master/hardware-mods/photo1.png)  
![image](https://github.com/ValCher1961/McDebian_WRT3200ACM/blob/master/hardware-mods/photo2.png)

The J13 connector for the fan can be selected at your discretion. The fan needs to use a 12 volt, as on the wrt1900ac model - "SUNON HA4010V4-0000-C99" or similar.

_**Attention!**_ Soldering of elements is carried out by an air soldering station with temperature control. For soldering, use a low-temperature solder (melting point not more than 190 degrees Celsius) and neutral flux. At the end of the work, clear all the soldering areas from the flux residue.

**Radiator**
The location of the fan installation on the radiator is shown in the drawing. Rework the radiator according to the drawing.
![image](https://github.com/ValCher1961/McDebian_WRT3200ACM/blob/master/hardware-mods/Radiator.png)

## 3. Fan effect
The processor temperature schedule when compiling the kernel on the WRT3200ACM router without using a fan.
![image](https://github.com/ValCher1961/McDebian_WRT3200ACM/blob/master/hardware-mods/fan_off.PNG)
The processor temperature schedule when compiling the kernel on the WRT3200ACM router using a fan. Setting T = 70°C.
![image](https://github.com/ValCher1961/McDebian_WRT3200ACM/blob/master/hardware-mods/fan_on.PNG)
