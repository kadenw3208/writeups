# Torrent Analyze
Category: Crypto
Points: 400
## Problem Description
SOS, someone is torrenting on our network.One of your colleagues has been using torrent to download some files on the company’s network. Can you identify the file(s) that were downloaded? The file name will be the flag, like  `picoCTF{filename}`.  [Captured traffic](https://artifacts.picoctf.net/c/165/torrent.pcap).
## Writeup
After playing around with the file for a bit, we can't find anything, so we look at the hint, and we come across hint #2:
`You may want to enable BitTorrent protocol (BT-DHT, etc.) on Wireshark. Analyze -> Enabled Protocols`
<br>We can do a quick search for `bt-dht` in our wireshark, and we come across this:
![im.1](https://i.ibb.co/rxYDhVW/image.png)
We can see in the bottom right that `info_hash` is a keyword. we do a quick search for the hex value of `hash (68 61 73 68)`. This is what comes up: 
![bruh](https://i.ibb.co/ZVyhLgD/image.png)
Now, with the filter, we can just go through the info hash of each until eventually we will find a file that ends with `.iso` (hint #4). 
<br> `picoCTF{ubuntu-19.10-desktop-amd64.iso}`
