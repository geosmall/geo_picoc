picoc - Copied from: https://gitlab.com/zsaleeba/picoc
-----

PicoC is a very small C interpreter for scripting. It was originally written 
as a script language for a UAV's on-board flight system. It's also very 
suitable for other robotic, embedded and non-embedded applications.

The core C source code is around 3500 lines of code. It's not intended to be 
a complete implementation of ISO C but it has all the essentials. When 
compiled it only takes a few k of code space and is also very sparing of 
data space. This means it can work well in small embedded devices. It's also 
a fun example of how to create a very small language implementation while 
still keeping the code readable.

picoc is now feature frozen. Since it's important that it remain small it's 
intended that no more major features will be added from now on. It's been 
tested on x86-32, x86-64, powerpc, arm, ultrasparc, HP-PA and blackfin 
processors and is easy to port to new targets. 


Compiling picoc
---------------

picoc can be compiled for a UNIX/Linux/POSIX host by typing "make".

The test suite can be run by typing "make test".


Porting picoc
-------------

platform.h is where you select your platform type and specify the includes 
etc. for your platform.

platform_XXX.c contains support functions so the compiler can work on 
your platform, such as how to write characters to the console etc..

platform_library.c contains your library of functions you want to make 
available to user programs.

There's also a clibrary.c which contains user library functions like 
printf() which are platform-independent.

Porting the system will involve setting up suitable includes and defines 
in platform.h, writing some I/O routines in platform_XXX.c, putting 
whatever user functions you want in platform_library.c and then changing 
the main program in picoc.c to whatever you need to do to get programs 
into the system.

platform.h is set to UNIX_HOST by default so tests can be easily run on
a UNIX system. You'll need to specify your own host setup dependent on 
your target platform.


Copyright
---------

picoc is published under the "New BSD License".
http://www.opensource.org/licenses/bsd-license.php


Copyright (c) 2009-2011, Zik Saleeba
All rights reserved.

Redistribution and use in source and binary forms, with or without 
modification, are permitted provided that the following conditions are 
met:

    * Redistributions of source code must retain the above copyright 
      notice, this list of conditions and the following disclaimer.
      
    * Redistributions in binary form must reproduce the above copyright 
      notice, this list of conditions and the following disclaimer in 
      the documentation and/or other materials provided with the 
      distribution.
      
    * Neither the name of the Zik Saleeba nor the names of its 
      contributors may be used to endorse or promote products derived 
      from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS 
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT 
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR 
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT 
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, 
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT 
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY 
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT 
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE 
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
