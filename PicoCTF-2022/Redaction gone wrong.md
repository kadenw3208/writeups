# Redaction gone wrong
Category: Forensics
Points: 100
## Problem Description
Now you DON’T see me.This  [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf)  has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?
## Writeup
When we open up the file, we see a bunch of black lines. But when we copy and paste the first line, the text `Breakdown` appears. Therefore, we can just copy paste the entire thing! This is what we get: <br>
```
Breakdown - Just painted over in MS word. Cost Benefit Analysis Credit Debit This is not the flag, keep looking Expenses from the picoCTF{C4n_Y0u_S33_m3_fully} Redacted document.
```
We can see our flag.
<br>
`picoCTF{C4n_Y0u_S33_m3_fully}`
