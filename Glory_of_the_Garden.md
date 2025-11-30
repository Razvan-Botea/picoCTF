# Description

This file contains more than it seems. Get the flag from [garden.jpg](https://challenge-files.picoctf.net/c_fickle_tempest/6013221da747114c37db29c554381dbe4bb4e746cf6bd880f9c3b5d0b495a823/garden.jpg).

# Solution

- looking at the image, there is nothing useful
- using nano to look at the code, still nothing
- using exiftool to see the metadata, still nothing useful
- but if i use strings to extract the readable characters from the binary data, i get the flag

# Flag

- **picoCTF{more_than_m33ts_the_3y339140129}**


