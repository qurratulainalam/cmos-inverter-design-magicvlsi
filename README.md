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
# cmos inverter:  
A CMOS inverter contains a PMOS and a NMOS transistor connected at the drain and gate terminals, a supply voltage VDD at the PMOS source terminal, and a ground connected at the NMOS source terminal, were VIN is connected to the gate terminals and VOUT is connected to the drain terminals.  
It is important to notice that the CMOS does not contain any resistors, which makes it more power efficient that a regular resistor-MOSFET inverter.As the voltage at the input of the CMOS device varies between 0 and 5 volts, the state of the NMOS and PMOS varies accordingly. If we model each transistor as a simple switch activated by VIN, the inverter’s operations can be seen very easily:  
![CMOS Inverters](https://user-images.githubusercontent.com/81563886/115317443-028e2080-a195-11eb-8b1c-6b0f1298f835.png)  
# Designing a CMOS inverter on magic VLSI layout tool:   
Below is the picture of the inverter I designed:   
![Screenshot from 2021-04-20 02-17-12](https://user-images.githubusercontent.com/81563886/115318268-dbd0e980-a196-11eb-8fc8-277c04b1212b.png)  
Writing the whole procedure of how I designed the inverter on magic would make this README file very long and drawn out so i am attaching a link with step by step tutorial for inverter layout **http://www-scf.usc.edu/~ee577/tutorial/magic_tut.html** 
**note:**
 I am not a professional physical chip layout engineer and the content of this repository may not reflect any industry standard. Errors, even obvious ones, may be presented without proper indication.





