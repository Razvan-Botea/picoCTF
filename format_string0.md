# Description

Can you use your knowledge of format strings to make the customers happy? Download the binary [here](https://artifacts.picoctf.net/c_mimas/69/format-string-0). Download the source [here](https://artifacts.picoctf.net/c_mimas/69/format-string-0.c). Connect with the challenge instance here: `nc mimas.picoctf.net 60690`

# Solution

- when i connect to the server, i get asked to choose from three options, and input one of them
	- Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
- for this first part, this is the code:
	```C
	int count = printf(choice1);  // FORMAT STRING VULN!
	if (count > 2 * BUFSIZE) {    // Need printf to return > 64
	    serve_bob();
	}
	```
- `printf` returns the number of characters printed
- i need `printf` to return a value greater then 64
- the only option from the three available that can do that is `Gr%114d_Cheese`
	- `%114d` prints a decimal integer with width 114

- for the second part, the flag is printed in the sigsegv_handler:
```C
void sigsegv_handler(int sig) {
    printf("\n%s\n", flag);  // PRINTS FLAG!
    fflush(stdout);
    exit(1);
}
```
- i need to cause a segmentation fault in serve_bob() by using format strings to write to invalid memory
- for this, i will choose an input with a lot of `%s` format specifiers: **Cla%sic_Che%s%steak**
- these will read strings from stack addresses;  eventually, it will hit an invalid address causing SIGSEGV, and printing the flag

# Flag

- flag: **picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_dc0f36c4}**
