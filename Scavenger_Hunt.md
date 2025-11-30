# Description

There is some interesting information hidden around this site [http://mercury.picoctf.net:27278/](http://mercury.picoctf.net:27278/). Can you find it?

# Solution

- first I use Ctrl+U to check the HTML code of the page and find the first part of the flag
- then i go to the CSS file used in the code and find the second part
- then i check the JavaScript file and get a clue about Google indexing the site that makes me think about the robots.txt file so i check to see if there is something interesting there
- there i find a comment that says this is an apache server, so i try some common apache files in the URL
	- at /.htaccess i find the next part of the flag and the last clue 'I love making websites on my Mac, I can Store a lot of information there.'
- this tells me i need to look for common Mac storage file names and i find the last part of the flag at ./DS_Store

# Flag

- picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_a69684fd}
