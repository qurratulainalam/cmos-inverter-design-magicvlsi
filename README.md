# cmos-inverter-design-magicvlsi

## Introduction to Magic VLSI:
Magic is a Very-large-scale integration (VLSI) layout tool originally written by John Ousterhout and his graduate students at UC Berkeley.
 Magic VLSI is a open source software for physical chip layout.Magic currently runs under **Linux**, although versions exist for DOS, OS/2, and other operating systems.  
 Magic is frequently used in conjunction with **IRSIM** and other simulation programs.  
 I would recommend to get Magic VLSI from the latest sources:https://github.com/libresilicon/magic-8.2   
 and also check these websites for further details:  
  http://opencircuitdesign.com/magic/  
  http://vlsi.csl.cornell.edu/magic/  
  http://www.research.digital.com/wrl/magic/magic.html  
 In order to open the layout of a cell, do the following:  
 1. **For starting up magic:** Magic uses its own internal ASCII format for storing cells in disk files. Each cell name is stored in its own file, named **name.mag**.    
* The first line in a **.mag** file is the string to identify this as a Magic file.  
**magic**  
* The next line is optional and is used to identify the technology in which a cell was designed. If present, it should be of the form  
**tech** techname (the technology we used is ***scmos** and **sample6m**)  
*  If absent, the technology defaults to a system-wide standard, currently **nmos**.  
2. **For selecting a file:** In the top menu-bar select File > Open and navigate to one of the *.mag files from the examples, e.g. INVERTER.mag  
3. Select a *.mag file and click Open. The layout of the selected cell will be show in the main window called **top level**  
4. **For editing the layout:** you can edit the layout by entering commands in the command window called **tkcon 2.3 main**  
5. Further tutorials for Magic can be found here http://opencircuitdesign.com/magic/tutorials/tut1.html.  
# CMOS Inverter:  
A CMOS inverter contains a PMOS and a NMOS transistor connected at the drain and gate terminals, a supply voltage VDD at the PMOS source terminal, and a ground connected at the NMOS source terminal, were VIN is connected to the gate terminals and VOUT is connected to the drain terminals.  
It is important to notice that the CMOS does not contain any resistors, which makes it more power efficient that a regular resistor-MOSFET inverter.As the voltage at the input of the CMOS device varies between 0 and 5 volts, the state of the NMOS and PMOS varies accordingly. If we model each transistor as a simple switch activated by VIN, the inverter’s operations can be seen very easily:  
![CMOS Inverters](https://user-images.githubusercontent.com/81563886/115317443-028e2080-a195-11eb-8b1c-6b0f1298f835.png)  
# Designing a CMOS inverter on magic VLSI layout tool:   
Below is the picture of the inverter I designed:   
![Screenshot from 2021-04-20 02-17-12](https://user-images.githubusercontent.com/81563886/115318268-dbd0e980-a196-11eb-8fc8-277c04b1212b.png)  
Writing the whole procedure of how I designed the inverter on magic would make this README file very long and drawn out so i am attaching a link with step by step tutorial for inverter layout **http://www-scf.usc.edu/~ee577/tutorial/magic_tut.html**  
# Testing the inverter with IRSIM:  
After the completion of the drawing in Magic we basically need to extract the code of the drawing to test and see if we are getting the requried results and if the gate is working properly or not. This code includes the values of parasitic capacitors appear in the metal connections of the transistors, width to length ratios of the transistors and so on.This extraction can be done easily by **extract all** command. Then a file which has an extension of **.ext** will be saved to the common direction. However this **.ext** file is not usable for us, therefore we need to use **ext2sim** command to obtain the code of the magic layout design.THhe following file will be in **.sim**  extension and it can be viewed by **text editor** in linux.lets see what IRSIM really is :  
## IRSIM:  
IRSIM is a tool for simulating digital circuits. It is a "switch-level" simulator; that is, it treats transistors as ideal switches. Extracted capacitance and lumped resistance values are used to make the switch a little bit more realistic than the ideal, using the RC time constants to predict the relative timing of events.  
IRSIM shares a history with magic, although it is an independent program. Magic was designed to produce, and IRSIM to read, the **".sim"** file format, which is largely unused outside of these two programs.  
**HOW IRSIM WORKS:**  
* The basic idea of IRSIM is that you tell it which nodes to pull high, which nodes to pull low, which nodes to tristate, and then you tell IRSIM to run the simulation for a certain period of time. This period of time is the stepsize.The stepsize we used in the inverter's stimulation is 50nanoseconds. The default stepsize is 10 nanoseconds.  
**stepsize 50**  
* Because not all power supplies are so obviously labeled, it is necessary to provide power to your circuit by declaring the power supply ("vdd") to be logic high and ground ("gnd") to be logic low. This may seem trivial, but the simulation won't work without it.  
**h vdd**  
**l gnd**  
* The command 'w' tells IRSIM to watch the following nodes.  
 **w a b**  
* d displays all the nodes that are being watched. You can also enter in something like 'd a ' which tells IRSIM to only display nodes a and b at time zero, the values of the nodes are all undefined   
**d**  
* The l command forces the nodes to a logic low value of 0 The command below sets node a  to logic 0   
**l a**  
* s tells IRSIM to simulate for a certain period of time previously defined by the stepsize command. The default value is 10 ns, but we set it to 50ns above.  
**s**  
* IRSIM displays the values of the nodes after each step because of the previous d command. The current time is also displayed. Note that time = 50 ns. This is the current simulation time now.  
**a=0  b=1  
time = 50.000ns**  
* h sets the following nodes to a logic high value. Therefore the above command sets node c to logic 1.  
**h a**  
* same steps will be repeated again for logic high value  
* IRSIM has a built-in graphical logic analyzer which lets you view waveforms. The 'analyzer' command sets up the analyzer window.the following command will tell IRSIM to display the nodes a and b in the analyzer window  
**ana a b  
OR  
analyzer a b**  
* IMPORTANT, When you set a node high or low using the h or l commands, the node keeps being set to high or low (no matter what the circuit is trying to do to the node!) until you use the x command to stop setting the node. 



**note:**  
 I am not a professional physical chip layout engineer and the content of this repository may not reflect any industry standard. Errors, even obvious ones, may be presented without proper indication.  
 





