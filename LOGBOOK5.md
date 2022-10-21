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
    - To exploit this vulnerability first and most important we need to find the distance between the buffer`s starting position and the place where the return-adress is stored.After finding this information we must change the return adress to a position where we have our shellcode.
    - Finding the distance between the buffer`s starting position and return adress with gdb:
        - First set a break point at bof().
        - The program stops before the ebp register is pointing to the current stack frame. Using the gdb's 'next'  command we can get the current stack frame and the buffer`s adress.
        (meter foto do gdb )
        - ebp -> 0xffffca68
        - buffer -> 0xffffc9fc
        - Using this values we can represent our stack and calculate the offset between the buffer`s starting point and the return address:
        (meter foto stack)
    
    - The next step is to prepare our payload, we will be using the following python script:
        (meter foto python script)
        - First the payload is filled with NOP's.
        - The shellcode will be allocated to the end of the buffer. This way the start variable is the size of the buffer (517 bytes) minus the shellcode size.
        - The frame pointer obtained from the gdb is different form the actual pointer because gdb has pushed some environment data before runnig the debugged program, therefore, the frame pointer will be larger. We approach this problem with brute force, after a few tries we found that adding 0xd0 to our return address was enough to complete succesfuly our exploit. 
        - As we can see explained in our stack representation, 112 bytes is the offset between the start of the buffer and the return address: (100 buf bytes + 8 local variables bytes + 4 ebp bytes )
    - Lauching the attack successfully:
      (meter foto execução e a shell a ser lançada com permissao root)
