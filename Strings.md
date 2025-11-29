# Description

Can you find the flag in file without running it?

# Solution

- we get a binary file
- if we want to get the readable content of a binary file we can use the `strings` command
- we get a bunch of random characters, and we can use `grep` to find the flag
- `strings strings | grep "picoCTF"`

# Flag

- flag:**picoCTF{5tRiNg5_1T_827aee91}**
