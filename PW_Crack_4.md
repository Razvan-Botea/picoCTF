# Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/60/level4.py) and you’ll need the encrypted [flag](https://artifacts.picoctf.net/c/60/level4.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/60/level4.hash.bin) in the same directory too. There are 100 potential passwords with only 1 being correct. You can find these by examining the password checker script.

# Solution

- we get a password checker and a long list of passwords
- we need to try all the passwords until we get the right one and get the flag
	```python
	for password in "8799" "d3ab" "1ea2" "acaf" "2295" "a9de" "6f3d"; do
	    if echo "$password" | python3 level3.py then
			echo "Password: $password"
			break
		fi
	done
	```
# Flag

- flag: **picoCTF{fl45h_5pr1ng1ng_d770d48c}**
