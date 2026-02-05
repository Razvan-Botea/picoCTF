# Description

People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate. `ssh -p 56404 ctf-player@rhea.picoctf.net` Using the password `84b12bae`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

# Solution

- Checksum: 3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4
- To decrypt the file once you've verified the hash, run `./decrypt.sh files/<file>`.

- after connecting to the server, i see three files:
	- checksum.txt, containing the checksum provided in the description
	- decrypt.sh, which contains the decryption script
	- files, which contains a lot of files
- the goal is to find which of these files matches the given SHA-256 hash, then decrypt it to get the flag

- **sha256sum files/* | grep -i "b09c99"**
	- calculates the SHA-256 hash for every file in the files/ directory
	- search for the hash matching the checksum
	- return the good file

- then i can use the decryption script to get the flag

# Flag

- **picoCTF{trust_but_verify_e018b574}**
