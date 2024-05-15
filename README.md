# thd.py

thd.py is a program to calculate Total Harmonic Distortion from a signal which is taken from a Siglent oscilloscope while also showing a live Fast Fourier Transform display and showing markers for fundamental and harmonic frequencies.

A screen recording of a typical out is shown in thd.mps in the folder resources/.

This program has been tested on a Siglent SDS1202X-E oscilloscope, but is supposed to work on any SDS1000 and SDS2000 series oscilloscopes from Siglent. This is determined by the pydatacq package which is imported by thd.py.


## communication

The program communicates SCPI over ethernet with the oscilloscope, ie. the oscilloscope needs to be connected to ethernet and have an ip-address known to the user. The ip address can be entered on the commandline to start the the program.


## frequency input

Frequency input on the commandline can be done in human legible form, like 97.5M for 97500000, or 1.5k for 1500. This is done using the package 'quantiphy'.



Entering `python3 thd.py --help` will show the following information:

```
usage: thd.py [-h] -C {1,2} [-f0 FREQ] [-max_f FREQ] [-f FLOOR] -ip IP [-port PORT] [-t NAME] [-w NAME]
              [-fps]

Display FFT and calculate THD for a channel on Siglent SDS1202X-E oscilloscope.

options:
  -h, --help            show this help message and exit
  -C {1,2}              channel to display (default: None)
  -f0 FREQ              fundamental frequency (in Hz) (default: 1k)
  -max_f FREQ           maximum frequency to display / use for calculations (in Hz) (default: 25k)
  -f FLOOR, --floor FLOOR
                        minimum level of harmonics (in dBvrms) (default: -85)
  -ip IP                ip address of the oscilloscope (default: None)
  -port PORT            port on which the oscilloscope is listening (default: 5025)
  -t NAME, --title NAME
                        plot title (default: None)
  -w NAME, --window NAME
                        window title (default: None)
  -fps                  show waveform updates per second (default: False)
```


## requirements

The following packages are required for fft.py to run:

- pydatacq
- numpy
- scipy
- quantiphy
- matplotlib
- uvloop


