## Description

Know of little and big endian? [Source](https://artifacts.picoctf.net/c_titan/117/flag.c)
Additional details will be available after launching your challenge instance.

**Endianness** refers to the byte order used to store multi-byte data types (like integers, floats) in computer memory.
Big-endian = most significant byte stored at the lowest memory address; like reading left-to-right
Small-endian = least significant byte stored at the lowest memory address

## Solution

- i get a program that computes the big endian and small endian representation of a word and then asks the user to input these values and compares it's values with the user's
- if they are both correct, the program outputs the flag
- i use cyberchef to convert the given word to hex and then just input the reverse order of the bytes for little endian and the normal order for big endian, and get the flag:

## Flag

- **picoCTF{3ndi4n_sw4p_su33ess_25c5f083}**
