# Description

A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?

# Solution

- we connect with netcat to a server and get three separate hashes that we have to crack 
- i used the Crackstation site to do this and got:
	- 482c811da5d5b4bc6d497ffa98491e38 => password123
	- b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3 => letmein
	- 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745 => qwert098

# Flag

- picoCTF{UseStr0nG_h@shEs_&PaSswDs!_5b836723}
