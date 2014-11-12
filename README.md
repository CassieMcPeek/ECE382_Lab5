ECE382_Lab5
===========

# Lab 5 - Interrupts - "Remote Control Decoding"

# Purpose
  In this lab, we used our knowledge of interrupts and the Timer_A subsystem to reverse engineer a remote control. We used the timer interrupt and the general purpose pin interrupt to decode a remote control. The purpose of 
  day 1 was to learn the timing and bit patterns of our remote controls. Day 2, we were to demonstrate that our code can receive and decode button presses from our remote controls. Day 3 we were to implement either our etch-a-sketch or pong game. I utilized remote 5 for the functionality of this lab. For the prelab, I used remote 6. I ran into a lot of problems with remote 6, which is why I changed for the funcitonality.  The last table reflects the correct code for the buttons on remote 5; however, the first two tables reflect the results of remote 6 with the logic analyzer. I had to re-do the logic analyzer portion with remote 5 to obtain the correct values
  
  
# Day 1
1. 	How long will it take the timer to roll over? 
	
	(0xFFF cnts)/rollover*  (8 clks)/(1 cnt)*  (1 us)/(8 clks)   = 0xFFFF us/rollover

2. 	How long does each timer count last?

	(1 cnt)/1*  (8 clks)/(1 cnt)*  (1 us)/(8 clks) = 1 cnt = 1 us

The while(1) loop in main reads in the ir pules in the for loop. 
Annotate the picture below to indicate which line of the for loop in the program is executed at which part of the pulse. You should show a total of 6 lines of code (lines 32-34 and lines 36-38).

![alt text] (https://raw.github.com/CassieMcPeek/ECE382_Lab5/master/Day_1_Picture.jpg "Logic Analyzer")

List the lengths of the pulses generated by the remote control in absolute time using the O'scope (3 significant figures) and in timer A counts. Note: "start logic 0 half-pulse" refers to the logic LOW portion of the start pulse, and "data 0 logic 1 half pulse" refers to the second half (which is a logic HIGH) of the pulse representing a zero bit.

![alt text] (https://raw.github.com/CassieMcPeek/ECE382_Lab5/master/Day_1_Table_1.JPG "Logic Analyzer")


Collect and tabulate in Excel 8 samples of timer A counts for each of the following pulse types (in decimal). Compute the average and standard deviation of each pulse type. I would suggest just grabbing it from the CCS variables tab.
- Data 1, logic 1 half-pulse - Data 0, logic 0 half-pulse - Data 0, logic 1 half-pulse
Ensure you label the rows and columns of your table so that I will know what the information in each cell means.

![alt text] (https://raw.github.com/CassieMcPeek/ECE382_Lab5/master/Day_1_Table_2.JPG "Logic Analyzer")

 For each pulse type list the range of timer A counts that would correctly classify 99.9999426697% of the pulses. This number has something to do with the standard deviation (hint: look at the table in this section).
The count would that would classify 99.9999426697% of the pulses would be two standard deviations.

	Data 1 Logic 1 range = (1594.5  to 1732.3)
	Data 0 Logic 0 range = (505.6 to 601.1)
	Data 0 Logic 1 range = (560.2 to 591.8)
	
Write the codes (in hex) for several remote control buttons.

![alt text] (https://raw.github.com/CassieMcPeek/ECE382_Lab5/master/Day_1_Table_3.JPG "Logic Analyzer")

# Day 2/Required Functionality

There were multiple challenges I faced throughout this lab. The first was that I ran into a lot of problems with remote 6, which is why I changed for the functionality.  The last table in the prelab reflects the correct code for the buttons on remote 5; however, the first two tables reflect the results of remote 6 with the logic analyzer. I had to re-do the logic analyzer portion with remote 5 to obtain the correct values, and those values are utilized in the required funcitonality code. 

The hardware schematic for required functionality is below.

![alt text] (https://raw.github.com/CassieMcPeek/ECE382_Lab5/master/Schematic.JPG "Logic Analyzer")

Once I had the MSP430 all hooked up, I began with the given files, start5.c and start5.h. The first part that I ran into trouble with, was I forgot to change the values in the header file to the correct values for my remote. I was debugging, and with the help of breakpoints, I knew that my code was responding to the button presses, but it was not toggling the LED like I wanted it to. After playing around with my code, C2C Ian Goodbody told me to double check the values in my header file. After looking at those again, I realized that they were the values for remote 6 and I was now using remote 5. Looking back, it probably would have been easier to just use rmeote 6 the entire lab, but at that point I had already done the logic analyzer part for remote 5 so I continued on with that. Below are the correct values for remote 5 in the header file. 
		#define		averageLogic0Pulse	450 
		#define		averageLogic1Pulse	0x05DF
		#define		averageStartPulse	22500 
		#define		minLogic0Pulse		averageLogic0Pulse - 200 
		#define		maxLogic0Pulse		averageLogic0Pulse + 200 
		#define		minLogic1Pulse		averageLogic1Pulse - 200 
		#define		maxLogic1Pulse		averageLogic1Pulse + 200 
		#define		minStartPulse		averageStartPulse - 1000 
		#define		maxStartPulse		averageStartPulse + 1000 

		#define		PWR		0xC2D0 
		#define		ONE		0xC284 
		#define		TWO		0xC244 
		#define		THR		0xC2C4 

		#define		VOL_UP	0xC228 
		#define		VOL_DW	0xC2A8 
		#define		CH_UP	0xC298 
		#define		CH_DW	0xC218 


