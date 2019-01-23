<<<<<<< HEAD
This is the git repository for Linux kernel drivers (and driver modifications)
we use for IEEE 802.11n research.

The tool was released on November 8, 2010, and was announced to the SIGCOMM
community in the January 2011 issue of CCR.  See our tool announcement for
more information:

   Daniel Halperin, Wenjun Hu, Anmol Sheth, and David Wetherall. "Tool Release:
   Gathering 802.11n Traces with Channel State Information." ACM SIGCOMM
   Computer Communication Review (CCR), vol. 41, no. 1, p. 53, January 2011.
   http://ccr.sigcomm.org/online/?q=node/719

This includes the 802.11n Channel State Information (CSI) Measurement Tool we
have used in our SIGCOMM, GLOBECOM and CCR papers:

   Daniel Halperin, Wenjun Hu, Anmol Sheth, and David Wetherall. "Predictable
   802.11 Packet Delivery from Wireless Channel Measurements." ACM SIGCOMM,
   2010.

   Daniel Halperin, Wenjun Hu, Anmol Sheth, and David Wetherall. "802.11n With
   Multiple Antenna For Dummies." ACM SIGCOMM Computer Communication Review
   (CCR), vol. 40, no. 1, pp. 19–25, January 2010.

   Eldad Perahia, Anmol Sheth, Thomas Kenney, Robert Stacey, and Daniel
   Halperin. "Investigation into the Doppler component of the IEEE 802.11n
   channel model." IEEE GLOBECOM -- Wireless Communications, 2010.

For more information, see our project website at:

   http://r.halper.in/url/csitool

Contact:

   Daniel Halperin   ---   dhalperi@cs.washington.edu
   Graduate Student, University of Washington Computer Science and Engineering
   http://r.halper.in/work
=======
galileo-linux-stable
====================

This is a kernel for Intel Galileo Gen1/2 which will be rebased on and will track Linux stable.

If your Galileo Gen1/2 project requires some of the latest kernel features then this might be the
Linux kernel for you.

How to build the kernel?

1.Build a cross-compiler toolchain with Yocto

http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-iot-devkit/

OR

2.Use a pre-built toolchain from IoT DevKit

https://software.intel.com/sites/landingpage/iotdk/linux-developement-kit.html

NOTE: You will need to execute the 'devkit-launcher' script distributed with IoT DevKit SDK
at least once before using the cross-compiler.

After you have built/downloaded the cross-compiler toolchain:

1.Include the cross-compilation tools in your PATH:

export PATH=path_to_sdk/sysroots/x86_64-pokysdk-linux/usr/bin/i586-poky-linux:$PATH


2.Cross-compile the kernel

ARCH=i386 LOCALVERSION= CROSS_COMPILE=i586-poky-linux- make -j8


3.Extract the kernel modules from the build to a target directory (e.g ../galileo-stable-install)

ARCH=i386 LOCALVERSION= INSTALL_MOD_PATH=../galileo-stable-install CROSS_COMPILE=i586-poky-linux- make modules_install


4.Extract the kernel image (bzImage) from the build to a target directory (e.g ../galileo-stable-install)

cp arch/x86/boot/bzImage ../galileo-stable-install/


5.Install the new kernel and modules from the target directory (e.g ../galileo-stable-install) to your micro SD card

5.1.Replace the bzImage found in the first partition (ESP) of your micro SD card with the one from your target directory (backup the bzImage on the micro SD card e.g. rename it to bzImage.old)

5.2.Copy the kernel modules from the target directory to the /lib/modules/ directory found in the second
partition of your micro SD card (e.g /lib/modules/3.18.1-galileo-g1)

6.Reboot into your new kernel

NOTE:
If you experience any issues with your custom-built kernel you can revert to you kernel backup from step 5.1

DISCLAIMER
This project is run on a best effort basis with no warranty and independent from my employer.
Hopefully it will be useful to someone and is provided "as is". The entire risk to the quality,functionality and
performance is with you. If it breaks, you get to keep both pieces.

>>>>>>> ab9272918528970820ceb8d8cee68dd5e2286cfe
