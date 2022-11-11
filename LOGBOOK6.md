# Tasks for week \#6

## CTF

### Challenge 1



## Format Strings Seed Labs

- **Task 1**:
    - The purpose of this task is to create a payload so that when the function myprintf is executed the server crashes. By analysing the program code, we verified that the function myprintf uses the function printf without format specifier. Thus, creating a payload with various "%.8x" and passing to the fuction myprintf the server will crash.


- **Task 2a**:
    - The purpose of this task is to print the stack. First, we need to choose 4 bytes to allocate in our payload  (0x12345678) to identify when we get to the stack. The rest of the payload is made by "%x". After some tries we found that it was necessary 64 "%x" to get to the value 0x12345678.


- **Task 2b**:
    - The purpose of this task is to print a secret message (string) from the heap. Through the server answers the address of that string was identified (0x080b4008). Then, our input was followed by 63 "%x" + 1 "%s" format specifiers which printed out the data on the stack and the secret message string, respectively.
 

- **Task 3a**:
    - The purpose of this task was to change the target value to a different value. First, we set the first 4 bytes of our payload as the first bytes of the target address given. Then, the payload was filled with 63 "%x" format specifiers and a "%n" which causes printf to load the number of characters that have been printed by printf before the "%n".


- **Task 3b**:
    - The purpose of this task was to change the target value to 0x5000. As we explained in task3a "%n" loads the number of characters that have been printed by printf before the "%n". Therefore, to change the target value to 0x5000 we need to print 20480 characters before the "%n". However, the maximum number of characters that we can input is 1500. In order to print 20480 characters we printed 63 "%x": the first 62 with 10 of left-pad and the last one with 19852. To that we add the 8 characters of the target's address. In total, it adds up to 20480 bytes which represents 0x5000 in hexadecimal. 



