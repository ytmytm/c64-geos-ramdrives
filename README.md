RamDrives drivers and auto-exec installer for GEOS 64/128
=========================================================

Maciej 'YTM/Elysium' Witkowiak
2001, 2014

#ABOUT
This is the source code for installer and drivers for GEOS 64/128 to utilize extra RAM as additional virtual disk drive. It is intended for setups *without REU*.

This source code can be assembled with ACME crossassembler into CVT file and put on GEOS disk image with c1541 tool (from VICE emulator).
http://sourceforge.net/projects/acme-crossass/

It should be easy to adapt this software to support any other kind of memory expansion as a RAM drive.

Two kinds of RAM expansions are supported:

##1. RamCart 128K
RamCart is a memory expansion quite similar to GeoRAM. It puts a 256-byte window of external battery-backuped memory into I/O space. This works for C64 and C128 in both 64 and 128 modes.

##2. C128 expanded to 256K
This is a memory expansion that enables C128 MMU to address 4 banks of memory instead of two. It is fully compatible with C128 addressing mode and page sharing.

#OPTIONS
The file init128rc.tas supports only RamCart device and can be configured to output auto-exec file for either GEOS64 or GEOS128.

The file init128iram.tas supports only C128 with 256K RAM and can be configured to additionally support also RamCart 128K. In full mode it will create a RAM drive with 256K of free space (128K from C128 internal memory and 128K from RamCart).

#ASSEMBLY

Please check the comments on top of init128iram.tas and init128rc.tas and assemble those files e.g.:
```
acme init128rc.tas
```

#INSTALLATION
After un-converting CVT files (or after writing D64 image with files unconverted by c1541 tool) just execute the application to add new drive to the system.

You can put it also on your bootdisk to have the RAM drive available at all times. Very important: *It has to be placed on a page behind CONFIGURE 64/CONFIGURE 128*.

#COPYING
This software is covered by GPL v2 license.
