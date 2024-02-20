
# ut61e (Python)

This is a fork of https://github.com/pklaus/ut61e_python


This is a Python package helping you to capture and interpret data from
the digital multimeter Uni-T UT61E. 

I've removed HID API from the original code, afaik it's only available in ut61e+.
I've kept data parsing and added direct reading from a serial port. Added a "one-shot" mode - the code 
reads measurements from a multimeter and exits.

## `es51922` – Interprets the output of the ES51922 chip

This utility interprets data sent by the Cyrustek ES51922 chip
used in the Uni-Trend digital multimeter UT61E.
It reads lines from the stdin or serial port, tries to interpret them as messages
from the chip and prints basic information on the stdout.
In addition, it writes a CSV file with a lot more information
to the working directory.

## Usage

Run `python3 ./ut61e/es51922.py --help` to see all command line arguments.

## Examples

To read data in a loop from a serial port and interpret it as Cyrustek ES51922 information:

`python3 ./ut61e/es51922.py --port /dev/cu.usbserial-1440`

Note that the "loop-mode" autocreates a CSV file, while the oneshot mode only writes to STDOUT


To read a single measurement, and put it in CSV format in STDOUT

`python3 ./ut61e/es51922.py --oneshot --port /dev/cu.usbserial-1440`


To read a single measurement in human-readable format, and put it in CSV format in STDOUT

`python3 ./ut61e/es51922.py --oneshot --mode readable --port /dev/cu.usbserial-1440`
