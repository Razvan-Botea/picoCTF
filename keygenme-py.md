# Description 

# Solution

- we get a python file that computes a secret key (the flag)
- we get the first half of the flag directly from the script: ```picoCTF{1n_7h3_|<3y_of_```
- the rest of the flag is computed using 8 if statements later in the program
- i can replicate that in my own program to get the full flag:
```python
import hashlib
username_trial = b"FREEMAN"

key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
key_part_dynamic1_trial = "xxxxxxxx"
key_part_static2_trial = "}"
key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial

print(hashlib.sha256(username_trial).hexdigest()[4]) 
print(hashlib.sha256(username_trial).hexdigest()[5])
print(hashlib.sha256(username_trial).hexdigest()[3])
print(hashlib.sha256(username_trial).hexdigest()[6])
print(hashlib.sha256(username_trial).hexdigest()[2])
print(hashlib.sha256(username_trial).hexdigest()[7])
print(hashlib.sha256(username_trial).hexdigest()[1])
print(hashlib.sha256(username_trial).hexdigest()[8])
```

# Flag

picoCTF{1n_7h3_|<3y_of_54ef6292}
