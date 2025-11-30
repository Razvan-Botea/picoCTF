# Description

Let's start off simple, can you overflow the correct buffer? The program is available [here](https://artifacts.picoctf.net/c/172/vuln). You can view source [here](https://artifacts.picoctf.net/c/172/vuln.c). Connect using: `nc saturn.picoctf.net 51064`

# Solution

- if i connect to the netcat connection, i am asked for some input
- if i enter 123 for example, the program exits without doing anything
- looking at the source code, i can see that it uses a 16 element vector to store the input, so maybe if i give it something longer than 16 characters, something interesting will happen
- i do that and i get the flag

# Flag

- picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}
