# Description

Can you find the flag? [shark1.pcapng](https://mercury.picoctf.net/static/ea41c400c3c7b4a63406e5e607d362ab/shark1.pcapng).

# Solution

- we get a wireshark packet capture
- after unsuccessfully trying  some filters, i decide to look for the least used protocols
	- i go to Statistics --> Protocol Hierarchy
- there, i see something interesting: under the HTTP protocol, there is line-based text data
- i apply it as a filter and get two packets
- in the second one there is a string that looks like an encoded flag, because of the curly brackets
- using Cyberchef, i decode it with the ROT13 cipher and get the flag

# Flag

- flag: **picoCTF{p33kab00_1_s33_u_deadbeef}**



