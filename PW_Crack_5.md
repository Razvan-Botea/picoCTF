# Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/79/level5.py) and you’ll need the encrypted [flag](https://artifacts.picoctf.net/c/79/level5.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/79/level5.hash.bin) in the same directory too. Here’s a [dictionary](https://artifacts.picoctf.net/c/79/dictionary.txt) with all possible passwords based on the password conventions we’ve seen so far.

# Solution

- this is similar to the previous exercise, but we get a dictionary file instead of just a list of passwords
- we need to iterate through the file and find the correct password
```python
import hashlib

correct_hash = open('level5.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

pos_pw = open('dictionary.txt', 'r').read().splitlines()

for pw in pos_pw:
        if hash_pw(pw) == correct_hash:
                print("The password is:" + pw)
                break
```

# Flag

- flag: **picoCTF{h45h_sl1ng1ng_36e992a6}**
