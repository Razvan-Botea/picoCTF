# Description

The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log. Download the encoded data here: [Logs Data](https://challenge-files.picoctf.net/c_amiable_citadel/34c1721086e2555cb8df9a09fcad35cfc09a2844bbc990dd022efca838b4e6ea/logs.txt). Be prepared—the file is large, and examining it thoroughly is crucial .

# Solution

- we get a really long log file
- decrypting it with base64 results in a image file
	- `base64 -d logs.txt > decoded.jpg`
- in the image there is a string of text
- this is in hex form, and using Cyberchef i translate it and find the flag

# Flag

- 'picoCTF{forensics_analysis_is_amazing_ac1e3584}'
