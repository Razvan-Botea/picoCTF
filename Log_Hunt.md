# Description

Our server seems to be leaking pieces of a secret flag in its logs. The parts are scattered and sometimes repeated. Can you reconstruct the original flag? Download the [logs](https://challenge-files.picoctf.net/c_amiable_citadel/49cec6157142f24a599f4164d5b63322c2494f801390d6f22eb91b3aa592bc66/server.log) and figure out the full flag from the fragments.

# Solution

- we get a file with a bunch of logs
- we can use the following line to find the distinct parts of the flag:
	- `cut -c23- server.log | grep "FLAGPART" | sort -u`
		- the first part removes the first 22 characters from each line of the file, as each line is a separate log that begins with date and time info, not important to me
		- then we find the lines containing the description FLAGPART, as those are the logs containing the flag
		- the last part prints in the terminal only the distinct logs, ignoring the duplicates
- after running this, we get the flag

# Flag

- **picoCTF{us3_y0urlinux_sk1lls_cedfa5fb}**


