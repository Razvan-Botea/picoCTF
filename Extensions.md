# Desccription

This is a really weird text file. Can you find the flag? Get the flag from [TXT](https://challenge-files.picoctf.net/c_fickle_tempest/31fe772e6a4c71e867af0b2a93818e06d8f8ebf8af2a9615495d00356ff576da/flag.txt).

# Solution

- we get what appears to be a .txt file
- if we open it with a text editor it is just a bunch of weird characters
- but if we use the `file` command, we see that it is actually a image file
- we can open it with an image editor like Gimp and we find the flag

# Flag

- **picoCTF{now_you_know_about_extensions}**
