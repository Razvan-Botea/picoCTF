# Description

Lyrics jump from verses to the refrain kind of like a subroutine call. There's a hidden refrain this program doesn't print by default. Can you get it to print it? There might be something in it for you. The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_verbal_sleep/63cac71f63ab95d9f131aa1b1177665a5e70f9a734ca46a68fe8b0eb3b02f052/lyric-reader.py). Connect to the program with netcat: `$ nc verbal-sleep.picoctf.net 59240`

# Solution

- we get a python script that prints lyrics from a song with interactive elements (user input)
- the flag is embedded in `secret_intro` at the very beginning of the song data, but the program starts at `[VERSE1]`, never printing this introductory section
- the program uses a `lip` (line index pointer) to navigate through the song lines
- the key vulnerability is in the `CROWD` interaction:
```python
elif re.match(r"CROWD.*", line):
    crowd = input('Crowd: ')
    song_lines[lip] = 'Crowd: ' + crowd  # VULNERABILITY: Direct assignment
    lip += 1
```

- the program has a special instruction for jumping to different lines:
```python
elif re.match(r"RETURN [0-9]+", line):
    lip = int(line.split()[1])  # Sets line pointer to arbitrary number
```
- this allows jumping to any line number in the song. Our goal: jump to line 0 where `secret_intro` is located.

- this line splits the current song line by semicolons, treating each part as a separate instruction. This is the injection point:
```python
for line in song_lines[lip].split(';'):
```

- with all this in mind, all i need to do to make the script print the part containing the flag is to insert this payload: `;RETURN 0` when asked for input
- using this, i get the flag

# Flag

- **picoCTF{70637h3r_f0r3v3r_0099cf61}**
