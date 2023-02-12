# read-dht22-temperature
An improved dht22 reader for raspberry pi zero.

The 'standard' reader code for the dht22 temperature sensor works well on faster processors like the Rapberry Pi 3B, but using it with a Pi Zero is less successful. The problem is that Linux steals time occasionally, despite setting maximum priority during the reading process, resulting in mis-timed pulses and even completely absent transitions.

This code is self-contained, so if you want to use the wiring pi libary it will need to be modified. The real-time clock is used to measure the time which elapses (or appears to elapse) between signal transitions, and then applies corrections for all the possible error scenarios, reducing the error (sumcheck failure) rate significantly.

To use this code, merely include it in your project and call 'init_read_temp()'. 
Subsquent calls to 'read_temp()' will return the current temperature.
There are no error conditions to report.

The code has been in use in my room thermostat, cylinder thermostat, and outside air temperature monitor projects for many years.
