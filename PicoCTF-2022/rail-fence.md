# rail-fence
Category: Crypto
Points: 100
Author: Kaden Wu

## Problem Description
A type of transposition cipher is the rail fence cipher, which is described  [here](https://en.wikipedia.org/wiki/Rail_fence_cipher). Here is one such cipher encrypted using the rail fence with 4 rails. Can you decrypt it?Download the message  [here](https://artifacts.picoctf.net/c/189/message.txt).Put the decoded message in the picoCTF flag format,  `picoCTF{decoded_message}`.
## Writeup
When we open up the file, we get this:
```
Ta _7N6D8Dhlg:W3D_H3C31N__387ef sHR053F38N43DFD i33___N6
```
After putting this into a rail fence cipher decoder, we get:
```
The·flag·is:·WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7
```

Flag: `picoCTF{WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7}`
