# Description

Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/7cf6a33f90deeeac5c73407a1bdc99b6/cat.jpg)

# Solution

- look at the metadata with exiftool: **exiftool cat.jpg**
- i can see that in the license field is a weird string of characters
- using Cipher Identifier, i see that it is base64 encoded
- trying to decode it i find the flag

# Flag

- **picoCTF{the_m3tadata_1s_modified}**


