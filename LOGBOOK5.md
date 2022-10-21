# Tasks for week \#5

- **Task 1**:
    - Compile code and execute
![task1.1](docs/logbook5/task1_ph1.png)

- **Task 2**:
    - The program has a vulnerability since the strcpy doesn't check sizes.
    - When our input file is bigger than the buf size, a buffer overflow occurs.
    - Since this program is root-owned SET-UID the user might be able to get a root shell while exploiting this buffer overflow.
![task2.1](docs/logbook5/task2_ph1.png)

- **Task 3**:
    - To exploit this vulnerability firstly and most importantly we need to find the distance between the buffer's starting position and the place where the return-adress is stored. After finding this information, we must change the return adress to a position where we have our shellcode.
    - To find the distance between the buffer's starting position and return adress with gdb:
        - First set a break point at bof().
        - The program stops before the ebp register is pointing to the current stack frame. Using the gdb's 'next'  command we can get the current stack frame and the buffer's adress.
        - ebp -> 0xffffca68
        - buffer -> 0xffffc9fc
![task3.1](docs/logbook5/task3_ph1.png)
![task3.2](docs/logbook5/task3_ph2.png)
![task3.3](docs/logbook5/task3_ph3.png)
![task3.4](docs/logbook5/task3_ph4.png)
        - Using this values we can represent our stack and calculate the offset between the buffer's starting point and the return address:
![task3.5](docs/logbook5/task3_ph5.png)
    
    - The next step is to prepare our payload, we will be using the following python script:
![task3.6](docs/logbook5/task3_ph6.png)
        - First the payload is filled with NOP's.
        - The shellcode will be allocated to the end of the buffer. This way the start variable is the size of the buffer (517 bytes) minus the shellcode size.
        - The frame pointer obtained from the gdb is different form the actual pointer because gdb has pushed some environment data before running the debugged program, therefore, the frame pointer will be larger. We approach this problem with brute force, after a few tries we found that adding 0xd0 to our return address was enough to complete succesfuly our exploit. 
        - As we can see explained in our stack representation, 112 bytes is the offset between the start of the buffer and the return address: (100 buf bytes + 8 local variables bytes + 4 ebp bytes )
    - Lauching the attack successfully:
![task3.7](docs/logbook5/task3_ph7.png)
