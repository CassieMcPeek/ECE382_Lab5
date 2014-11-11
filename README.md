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

