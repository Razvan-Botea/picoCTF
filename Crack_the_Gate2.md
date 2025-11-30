# Description

The login system has been upgraded with a basic rate-limiting mechanism that locks out repeated failed attempts from the same source. We’ve received a tip that the system might still trust user-controlled headers. Your objective is to bypass the rate-limiting restriction and log in using the known email address: `ctf-player@picoctf.org` and uncover the hidden secret. The website is running [here](http://amiable-citadel.picoctf.net:55085/). Can you try to log in?. Download the passwords list [here](https://challenge-files.picoctf.net/c_amiable_citadel/0fa9993f68e218c88707174fa41fb468619f09b372ccc6a563cc3c3446dedba5/passwords.txt).

# Solution

- like in the first challenge, we get a web page with a log in form
- but if we try a wrong password more than once it says we have to wait 20 minutes before trying again
- so the method used in the first challenge is not enough anymore
- the hints suggest reading about X-Forwarded-For
- this is a header that tells a web server the original IP address of a client connecting through a proxy or load balancer
- we can add this header to the request and use Burp Intruder to give it a different value for each request send
- we also give Intruder a list of passwords to try on each request
- this process results in a bunch of identical responses that tell the same thing: fail; but also a different response, with the flag, when the right password from the list is used

# Flag

- picoCTF{xff_byp4ss_brut3_f6cca7d4}
