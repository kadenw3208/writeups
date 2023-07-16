# Mr-Worldwide
Category: Crypto
Points: 200
Author: Kaden Wu
## Problem Description
A musician left us a [message](https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt). What's it mean?
## Writeup
Opening up the message, we get this:
```
picoCTF{(35.028309, 135.753082)(46.469391, 30.740883)(39.758949, -84.191605)(41.015137, 28.979530)(24.466667, 54.366669)(3.140853, 101.693207)_(9.005401, 38.763611)(-3.989038, -79.203560)(52.377956, 4.897070)(41.085651, -73.858467)(57.790001, -152.407227)(31.205753, 29.924526)}
```
These sure do look like coordinates!
Let's try putting them into Google Maps and taking the first character of each:
| **Coordinates**  |      **City** |
|:---------------------|:-----------|
|(35.028309, 135.753082)|**K**yoto|
|(46.469391, 30.740883)|**O**desa|
|(39.758949, -84.191605)|**D**ayton|
|(41.015137, 28.979530)|**I**stanbul|
|(24.466667, 54.366669)|**A**bu Dhabi|
|(3.140853, 101.693207)|**K**uala Lumpur|
|_|**_**|
|(9.005401, 38.763611)|**A**ddis Ababa|
|(-3.989038, -79.203560)|**L**oja|
|(52.377956, 4.897070)|**A**msterdam|
|(41.085651, -73.858467)|**S**leepy Hollow
|(57.790001, -152.407227)|**K**odiak|
|(31.205753, 29.924526)|**A**lexandria Governorate|

It seems like letters spell out Kodiak_Alaska, which is our flag!
`picoCTF{KODIAK_ALASKA}`


