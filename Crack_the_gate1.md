# Description

We’re in the middle of an investigation. One of our persons of interest, ctf player, is believed to be hiding sensitive data inside a restricted web portal. We’ve uncovered the email address he uses to log in: `ctf-player@picoctf.org`. Unfortunately, we don’t know the password, and the usual guessing techniques haven’t worked. But something feels off... it’s almost like the developer left a secret way in. Can you figure it out? The website is running [here](http://amiable-citadel.picoctf.net:53639/). Can you try to log in?

# Solution

- if we go to the site we find a login page
- I use Ctrl+U to look at the html code of the page
- near the end there is a weird comment that seems to be encrypted
- i use ROT13 and discover this:
	- NOTE: Jack - temporary bypass: use header "X-Dev-Access: yes"
- going back to the login page, i open the Dev tools and go to network
- i try to log in using the email and a random password
- in the Dev Tools i click in the request made by the login button and add a header with the discovered information, and then resend the request
- i get a response with the flag:

# Flag

- **picoCTF{brut4_f0rc4_b3a957eb}**

