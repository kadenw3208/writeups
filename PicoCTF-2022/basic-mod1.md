# Basic_mod1
Category: Crypto
Points: 100
Author: Kaden Wu
## Problem Description
We found this weird message being passed around on the servers, we think we have a working decryption scheme.Download the message  [here](https://artifacts.picoctf.net/c/129/message.txt).Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.Wrap your decrypted message in the picoCTF flag format (i.e.  `picoCTF{decrypted_message}`)
## Writeup
I wrote this script to help me decode the message:
```
#include <iostream>
#include <iomanip>
#include <algorithm>
#include <cmath>
#include <climits>
#include <string>
using namespace std;
int main()
{
	int arr[] = { 350,63,353,198,114,369,346,184,202,322,94,235,114,110,185,188,225,212,366,374,261,213 };
	string alphabet = "abcdefghijklmnopqrstuvwxyz";
	string digits = "0123456789";
	for(int i:arr){
		i %= 37;
		if (i <= 25) { cout << alphabet[i]; }
		else if (i > 25 && i < 36) { cout << i%26; }
		else { cout << "_"; }
	}
}
```
This code outputs:
`r0und_n_r0und_add17ec2`
Therefore, we have our flag:
`picoCTF{r0und_n_r0und_add17ec2}`
