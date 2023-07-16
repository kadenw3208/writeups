# Tapping
Category: Crypto
Points: 200
Author: Kaden Wu
## Problem Description
Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 48247`.
## Writeup
Once we enter in the challenge, we get this:
`.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. .---- ..--- -.... .---- ....- ...-- ---.. .---- ---.. .---- } `

This can be easily be recognized as Morse Code. We can use a Morse Code decoder to get our flag:
`PICOCTF#M0RS3C0D31SFUN1261438181#`
After putting this in flag format, we have our flag:
`picoCTF{M0RS3C0D31SFUN1261438181}`
