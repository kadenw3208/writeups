# file-run1
Category: Reverse Engineering
Points: 100
Author: Kaden Wu
## Problem Description
A program has been provided to you, what happens if you try to run it on the command line?Download the program  [here](https://artifacts.picoctf.net/c/218/run).
## Writeup
We can first copy the link address and download it into the webshell via the `wget` command. After we do that, we can apply  `chmod +x run` and `./run` to get our flag.
`picoCTF{U51N6_Y0Ur_F1r57_F113_9bc52b6b}`
