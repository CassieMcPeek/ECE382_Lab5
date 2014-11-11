ECE382_Lab5
===========

# Lab 5 - Interrupts - "Remote Control Decoding"

# Purpose
  In this lab, we used our knowledge of interrupts and the Timer_A subsystem to reverse engineer a remote control. We used the timer interrupt and the general purpose pin interrupt to decode a remote control. The purpose of 
  day 1 was to learn the timing and bit patterns of our remote controls. Day 2, we were to demonstrate that our code can receive and decode button presses from our remote controls. Day 3 we were to implement either our etch-a-sketch or pong game.
  
  
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
