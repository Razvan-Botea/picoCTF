# Description

Can you try to get the flag? Beware we have PIE! Connect to the program with netcat:
```sh
$ nc rescued-float.picoctf.net 59482
```
The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_rescued_float/104935b5fd5efcea1bc050d964ac91237c79eac916f57aef8e6407af232066ae/vuln.c). The binary can be downloaded [here](https://challenge-files.picoctf.net/c_rescued_float/104935b5fd5efcea1bc050d964ac91237c79eac916f57aef8e6407af232066ae/vuln).

# Solution

- we get a binary executable and its source code
- when i access the server with netcat, it gives me the address of the main function and asks me to input the address of the win() function to retrieve the flag
- the binary is compiled with PIE (Position Independent Executable), which means the function addresses will be random for each execution, but relative offsets between functions remain constant
- i need to find the address of the win() function

- first, i find the offset between main() and win() in the local binary:
	- `gdb ./vuln`
	- `(gdb) disassemble main`
	- `(gdb) disassemble win`
- calculate the offset: offset = main_address - win_address = 0x96
	- this offset is constant because it is determined at compile time
- all i have to do now is connect to the remote server, get the generated main() address, subtract 0x96 from it and enter this new value to get the flag

# Flag

- **picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_801240da}**
