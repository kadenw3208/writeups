# GDB Test Drive
Category: Reverse Engineering
Points: 100
Author: Kaden Wu
## Problem Description
Can you get the flag?Download this  [binary](https://artifacts.picoctf.net/c/86/gdbme).Here's the test drive instructions:

-   `$ chmod +x gdbme`
-   `$ gdb gdbme`
-   `(gdb) layout asm`
-   `(gdb) break *(main+99)`
-   `(gdb) run`
-   `(gdb) jump *(main+104)`
## Writeup
Just follow the instructions to get the flag.
`picoCTF{d3bugg3r_dr1v3_72bd8355}`
