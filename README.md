# HSV

## RGB to HSV and HSV to RGB colors system converstion tools.
```
This project provides the cython methods and C versions of the 
HSV conversion algorithms.

The code is based on the current python COLORSYS library, adapted and improved 
for an good increase in speed compare to the original model.

```
## Requirements: 
```
python >=3.0  
Cython 

Unlike most Python software, Cython requires a C compiler to be present on the system. 
The details of getting a C compiler varies according to the system used:

Linux The GNU C Compiler (gcc) is usually present, or easily available through the package system. On Ubuntu or Debian, for instance, the command sudo apt-get install build-essential will fetch everything you need.
Mac OS X To retrieve gcc, one option is to install Apple’s XCode, which can be retrieved from the Mac OS X’s install DVDs or from https://developer.apple.com/.
Windows A popular option is to use the open source MinGW (a Windows distribution of gcc). See the appendix for instructions for setting up MinGW manually. Enthought Canopy and Python(x,y) bundle MinGW, but some of the configuration steps in the appendix might still be necessary. Another option is to use Microsoft’s Visual C. One must then use the same version which the installed Python was compiled with.
The simplest way of installing Cython is by using pip:

pip install Cython
The newest Cython release can always be downloaded from https://cython.org/. Unpack the tarball or zip file, enter the directory, and then run:

python setup.py install
For one-time builds, e.g. for CI/testing, on platforms that are not covered by one of the wheel packages provided on PyPI, it is substantially faster than a full source build to install an uncompiled (slower) version of Cython with

pip install Cython --install-option="--no-cython-compile"

```
## Compilation:
```
You need to re-compile the file hsv.pyx after any change(s). 
Use the following:
C:\>python setup_hsv.py build_ext --inplace

This will translates Cython source code into efficient C code

If you change the file hsv_c you will also need to recompile the project 
```
## How to:
```
import the code in your program:

import HSV

# This will import the cython version 
from HSV import hsv2rgb, rgb2hsv

# This will import the C version 
from HSV import rgb_to_hsv_c, hsv_to_rgb_c

if __name__ == '__main__':
  r, g, b = 25, 60, 128
  rgb = rgb_to_hsv_c(r/255.0, g/255.0, b/255.0)


```
## Timings:
```
for 1000000 iterations
- cython   0.5401s  5.4e-07 (single)
- C        0.5241s  5.2e-07 (single) 
- Pure C   0.1540s  1.5e-07    -
- colorsys 2.1610s  2.1e-06    -
```

