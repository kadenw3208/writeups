# Includes
Category: Web Exploitation
Points: 100
Author: Kaden Wu

## Problem Description
Can you get the flag? Go to this  [website](http://saturn.picoctf.net:56469/)  and see what you can discover.

## Writeup
When we click on the " Say Hello" Button, it says:<br>
`"This code is in a separate file!"`
<br> Huh, that's interesting. We can go to Inspect Element and look through the files, slowly piecing the flag together. The first part of the flag is in `style.css` and the second part in `script.js`
`picoCTF{1nclu51v17y_1of2_f7w_2of2_b8f4b022}`
