# Description

Figure out how they moved the [flag](https://mercury.picoctf.net/static/88553d672efbccbc5868002f4c6eb737/tftp.pcapng).

# Solution

- we get a wireshark packet capture
- there are a lot of files, but most of them are blocks of data
- from the write requests we can see there are actually some files being transferred
- we can use the extract option in wireshark to get these files
	- we get two text files, 3 images and a .deb file
- the two text files contain what appears to be ciphered text, likely encrypted with ROT13
- using Cyberchef, i decrypt the message and get the following: 

```
TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN
I USED THE PROGRAM AND HID IT WITH-DUE DILIGENCE. CHECK OUT THE PHOTOS
```

- if we click on the .deb file from earlier, we see it is a steganography tool called steghide
- this is probably the program mentioned in the encrypted message
- if i try to use it on one of the pictures, it asks for a passphrase
- from the message, i can guess that the password is `DUEDILIGENCE`
- after trying this on the three pictures, i retrieve the flag from the third picture:

# Flag

- `picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}`
