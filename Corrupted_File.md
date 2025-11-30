# Description

This file seems broken... or is it? Maybe a couple of bytes could make all the difference. Can you figure out how to bring it back to life? Download the file [here](https://challenge-files.picoctf.net/c_amiable_citadel/10f12b1f51f0a73a50f6bd08cc2d0ef6b1e8039a27daac52f27b450dabeaec97/file).

# Solution

- we get a "data" file
- looking at the hex dump, we see something weird on the first line:
	- \x....JFIF......
- JFIF tells us this should be a jpeg file, but the magic byte is wrong
- changing it to **`FF D8 FF`** with hexedit 
- reopening the file we get a image with the flag

# Flag

- picoCTF{r3st0r1ng_th3_by73s_efd8c6c0}
