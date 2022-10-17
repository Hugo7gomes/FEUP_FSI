# Tasks for week \#5

- **Task 1**:
    - Compile code and execute
    (meter foto minha)

- **Task 2**:
    - The program has a vulnerability since the strcpy doesn't check sizes.
    - When our input file is bigger than the buf size, a buffer overflow occurs.
    - Since this program is root-owned SET-UID the user might be able to get a root shell while exploiting this buffer overflow.
    (meter foto 1)

- **Task 3**:
    - First set a break point at bof().
    - The program stops before the ebp register is pointing to the current stack frame. Using the gdb's 'next'  command we can get the current stack frame and the buffer`s adress.
    (meter foto do gdb )
    - ebp -> 0xffffca68
    - buffer -> 0xffffc9fc
    - Using this values we can represent our stack and calculate the offset between the buffer`s starting point and the return address:
    (meter foto stack)
    - The next step is to prepare our payload, we will be using the following python script.
    (meter foto python script)
    - First the payload is filled with NOP's.
    - The shellcode will be allocated to the end of the buffer. This way the start variable is the size of the buffer (517 bytes) minus the shellcode size.
    - The return address value will be the ebp address plus (ver como explicar o que fizemos) 
    - The offset is 112B 

