# SideChannel
Category: Forensics
Points: 400
Author: Kaden Wu
## Problem Description
There's something fishy about this PIN-code checker, can you figure out the PIN and get the flag?Download the PIN checker program here  [pin_checker](https://artifacts.picoctf.net/c/72/pin_checker)Once you've figured out the PIN (and gotten the checker program to accept it), connect to the master server using  `nc saturn.picoctf.net 50364`  and provide it the PIN to get your flag.
## Writeup
We can utilize the `time` command while also using pipes. We can use this command to see the time:
`echo [pin here] | time ./pin_checker`
<br> This command will let us see when the `user` field increases by a significant amount, we must have the right digit. We can keep testing like this, until we find that the pin is 	`48390513`
<br>
Flag: `picoCTF{t1m1ng_4tt4ck_9803bd25}`
