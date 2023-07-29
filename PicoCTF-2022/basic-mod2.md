# basic_mod2
Category: Crypto
Points: 100
Author: Kaden Wu
## Problem Description
A new modular challenge!Download the message  [here](https://artifacts.picoctf.net/c/179/message.txt).Take each number mod 41 and find the modular inverse for the result. Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.Wrap your decrypted message in the picoCTF flag format (i.e.  `picoCTF{decrypted_message}`)
## Writeup
This question really isn't that hard, just a small step up from the challenge basic_mod1. The edited code is shown here:

```
#include <iostream>
#include <iomanip>
#include <algorithm>
#include <cmath>
#include <climits>
#include <string>
using namespace std;
int modInverse(int a, int b) {
	for (int i = 1; i < b; i++) {
		if (((a % b) * (i % b)) % b == 1) {
			return i;
		}
	}
}

int main()
{
	int arr[] = { 104,372,110,436,262,173,354,393,351,297,241,86,262,359,256,441,124,154,165,165,219,288,42 };
	string alphabet = "abcdefghijklmnopqrstuvwxyz0123456789_";
	for(int i:arr){
		i %= 41;
		i = modInverse(i, 41);
		cout << alphabet[i-1];
	}
}
```
This gives us the result of:
`1nv3r53ly_h4rd_dadaacaa`
Thus, we have our flag:
`picoCTF{1nv3r53ly_h4rd_dadaacaa}`
