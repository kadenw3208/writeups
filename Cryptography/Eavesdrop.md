# Eavesdrop
Category: Forensics
Points: 300
## Problem Description
Download this packet capture and find the flag.

-   [Download packet capture](https://artifacts.picoctf.net/c/134/capture.flag.pcap)
## Writeup
When you first open up the packet capture in Wireshark and follow the TCP stream, you find:
```
Hey, how do you decrypt this file again?

You're serious?

Yeah, I'm serious

*sigh* openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123

Ok, great, thanks.

Let's use Discord next time, it's more secure.

C'mon, no one knows we use this program like this!

Whatever.

Hey.

Yeah?

Could you transfer the file to me again?

Oh great. Ok, over 9002?

Yeah, listening.

Sent it

Got it.

You're unbelievable
```
We see some `openssl` command, so we keep that for later. In the meantime, we continue searching around. In TCP stream #2, we find:
```
Salted__9B..'.b4.[..NX.mn.'-.rGs.....:..k..@.=6.
```
What could this be? We can download this in its raw form into a file called `file.des3`, which is what the openssl command requires. Then, we can run the command, cat out file.txt, and get the flag!
<br> `picoCTF{nc_73115_411_dd54ab67}    `
