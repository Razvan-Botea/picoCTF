# Description

Are overflows just a stack concern? Download the binary [here](https://artifacts.picoctf.net/c_tethys/29/chall). Download the source [here](https://artifacts.picoctf.net/c_tethys/29/chall.c). Connect with the challenge instance here: `nc tethys.picoctf.net 52237`

# Solution

- we get a binary that manages data on the heap
- the program has a "safe" variable that cannot be modified, but we need to do something with it to get the flag
- memory allocation in the program:
```C
#define INPUT_DATA_SIZE 5
#define SAFE_VAR_SIZE 5

input_data = malloc(INPUT_DATA_SIZE);
safe_var = malloc(SAFE_VAR_SIZE);
```
- win condition:
```C
void check_win() {
    if (strcmp(safe_var, "bico") != 0) {  // WIN if safe_var is NOT "bico"
        printf("\nYOU WIN\n");
        // Print flag
    }
}
```
- vulnerable function:
```C
void write_buffer() {
    printf("Data for buffer: ");
    fflush(stdout);
    scanf("%s", input_data);  // NO BOUNDS CHECKING!
}
```
- this function tries to add data to a variable with a buffer of only 5 bytes, without checking the length of the input
- this can result in a buffer overflow if the input is longer than 5 bytes
- if this happens, the additional data will leak into the bico variable, changing it and thus making the program printing the flag

- the program also let's me see the heap addresses:
```
[*]   0x652a6788e2b0  ->   pico    (input_data)
[*]   0x652a6788e2d0  ->   bico    (safe_var)
```
- this tells me that safe_var is 32 bits after input_var
- this means that if i input a value bigger than 32 bytes into input_var, some bytes will leak into safe_var, changing its value, and i get the flag

# Flag

- flag: **picoCTF{my_first_heap_overflow_c3935a08}**
