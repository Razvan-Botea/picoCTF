# Description

I wonder what this really is... "[enc](https://challenge-files.picoctf.net/c_wily_courier/c54640eb53abf2f31d27f53f1547faf619e26b013130e3b506905cdc8f9aea2d/enc) ''`.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`

# Solution

- for this challenge, i get a string containing unicode characters
- the description also tells me that each character encodes two original ASCII characters using bit manipulation
	- it takes two consecutive ASCII characters from the original string
	- converts each to its ASCII value
	- shift the first character 8 bits to the left
	- add the second character's value
	- convert the result back into a character
```
'A' = ASCII 65 = 01000001 (binary)
'B' = ASCII 66 = 01000010 (binary)

Encoding:
65 << 8 = 01000001 00000000 (16640)
+ 66    = 01000001 01000010 (16706)

chr(16706) = 'ꂂ' (some Unicode character)
```

- i made a python script that reverses this process:
```python
def decode(encoded_flag):
        decoded = ""
        for char in encoded_flag:
                code_point = ord(char)
                first_char = (code_point >> 8) & 0xFF
                second_char = code_point & 0xFF
                decoded += chr(first_char) + chr(second_char)
        return decoded

encoded = "灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸形㝦㘲捡㕽"
decoded = decode(encoded)
print (decoded)
```
- it takes each encoded character, one by one
- gets its Unicode code point (integer value)
- extract the 2 original ASCII values:
	- first character: (code_point >> 8) & 0xFF
	- second character: code_point & 0xFF
- the 0xFF is for discarding the first 8 bits of the 16 that comprise the original, encoded, character

# Flag

- **picoCTF{16_bits_inst34d_of_8_b7f62ca5}**
