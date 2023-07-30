# Sleuthkit Intro
Category: Forensics
Points: 100
## Problem Description
Download the disk image and use  `mmls`  on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into  `/tmp`  not your home directory.

-   [Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)
-   Access checker program:  `nc saturn.picoctf.net 52472`
## Writeup
Once you download the disk image, use `mmls disk.img.gz` to find the size of the partitions. We find this:
<br>
```
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```
We can see that the size of the partition for Linux is 202752. We enter that into the checker and get our flag.
<br>
`picoCTF{mm15_f7w!}`
