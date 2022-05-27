# Linux 5.17 kernel patch for (2022) XPS 15 9520 audio

[Original fix by Kristin Paget for the 9510 model](https://github.com/kristinpaget/xps-15-9510-audio)

The 2022-model XPS 15 appears to use the same 4-speakers-on-ALC289 audio setup as the Dell XPS 9510, so the woofers do not work by default.  This patch enables the same driver quirk to allow for much better audio quality and greater volume output.

Available as a .patch file (if you want to compile your own kernel) and a .deb package built from the 5.17.0 kernel using the supplied Ubuntu configuration (minus signatures, obviously). \

For folks looking to patch their own machines in similar ways, the ID numbers in the patch are the PCI SubVendor and SubDevice. 

Run
`lspci -vmnn` \
and look for your audio controller, it's likely to be at address 00:1f.3.  You want SVendor (likely 0x1028 for Dell machines) and SDevice; modify sound/pci/hda/patch_realtek.c accordingly.
