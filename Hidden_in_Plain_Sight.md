# Description

You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag. Download the jpg image [here](https://challenge-files.picoctf.net/c_amiable_citadel/a9f79ebd7dfa722721b5cbdd12a5059e9404c28c90b9b0bf9e307015f8c1c265/img.jpg)

# Solution

- we get a .jpg image
- using exiftool, we can look at the metadata for this picture
- nothing interesting there, except for s string of gibberish, that looks like an encrypted message
- i use Cipher Identifier to find the type of encryption. It is base64
- using cyberchef, i decrypt the text and get: `steghide:cEF6endvcmQ=`
- this tells me that i have to use steghide to uncover more information, and it looks like it is also giving me the passphrase
- however, it does no work as is, so i do an additional base64 decryption on the passphrase
	- i get the passphrase: `pAzzword`
- using this with steghide, i get the flag

# Flag

- `picoCTF{h1dd3n_1n_1m4g3_e7f5b969}`
