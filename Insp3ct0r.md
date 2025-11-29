# Description

Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/41511/`

# Solution

- if we go to the link and use `Ctrl+U` to see the HTML source code, we get the first third of the flag:
	- `picoCTF{tru3_d3`
- next, we go to the inspector with `Ctrl+Shift+I` --> Sources Tab --> mycss.css and find the next part of the flag
	- `t3ct1ve_0r_ju5t`
- then, in the inspector --> Sources Tab --> myjs.js, we find the fina; part of the flag:
	- `_lucky?f10be399}`

# Flag

- flag: **picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?f10be399}**
