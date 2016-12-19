Optotrak Application Programmer's Interface v3.7.1
for 32-bit Windows platforms.

Installation
------------
Run the install program SETUP.EXE from the CD to install the Windows version 
of the Optotrak API. The installation will copy the required library DLLs, 
install the export libraries and NDI include files required to build 
applications, and update the transputer TLD files in your '$ND_DIR$\realtime' 
directory.

New OPTOTRAK.INI settings
------------------------------------
The OPTOTRAK.INI file found in the '$ND_DIR$\settings' directory contains various 
Optotrak settings.  This version of the Optotrak API requires one new setting:

	[OPTOTRAK System]
	ResetTimeout = 1500
	
The 'ResetTimeout' value is the number of milliseconds that the software will
wait after the Optotrak System is reset before attempting to communicate
with the System Control Unit.  The Optotrak System requires a certain amount
of time to reset before it is able to accept more commands.


Compiling the sample programs
-----------------------------
The makefile SAMPLES.MAK can be used to compile the sample programs using
the Microsoft VC++ (5.0 or higher) 32-bit compiler. 
See the comments in the makefile for specific instructions on making the 
sample programs.
In addition there is a Visual Studio 2003 project file sample.vcproj in 
samples\vc directory. You can use it to build any of the samples using 
Visual Studio by replacing the content of the samples\vc\sample.c file 
with a particular sample code. 


Compiling application programs
------------------------------
You must include the appropriate header files in the include directory
NDLIB\INCLUDE in your application program source code. Export library OAPI.LIB
have been included for Borland C++ and Microsoft VC++. You must link your
application with the appropriate library. We have not tested the
export libraries with older 32-bit versions of these compilers.
You can also use Visual Studio 2003 project samples\vc\sample.vcproj as a template 
for your application using Optotrak API.

Running application programs
----------------------------
The DLL OAPI.DLL is installed by default in the '$ND_DIR$\programs' directory. 
This directory is added to the path and all your OAPI based applications will
find it there. 


Ethernet support for Windows applications
--------------------------------------------------------
You may choose to communicate with the Optotrak System using an ethernet
connection.  To access the Ethernet interface with your application programs,
add the following line to the [OPTOTRAK System] section of your OPTOTRAK.INI
file:

	Driver = etherlink.dll

and add the following section (with ID values appropriate to your system) to
your OPTOTRAK.INI file:

	[Ethernet Options]
	Server Address=172.16.1.104
	Control Port=9999
	Data Port=10000
	Data Timeout=10000
	Reset Delay=5000

The Parameter Data Timeout is the number of milliseconds allowed for
Ethernet commands to complete.  Commands taking longer are assumed to be
"stuck" and so will be aborted.


USB support for Windows applications
--------------------------------------------------------
To use a USB interface to communicate with the Optotrak System, change the
Driver value to:

		Driver = usblink.dll

================================================================================
Copyright 2011, Northern Digital Inc. 
Optotrak is a registered trademark of Northern Digital Inc.
Certus is a trademark of Northern Digital Inc.
NDI is a registered trademark of Northern Digital Inc.
Measurment You Can Trus is a trademark of Northern Digital Inc.
Product names listed are trademarks of their respective manufacturer.
Company names listed are trademarks or tradenames of their respective companies.
================================================================================
