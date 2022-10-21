# Tasks for week \#4

- **Task 1**:
  - Environment variables are a set of dynamic named values that can affect the way running processes will behave on a computer.
  - Using the command printenv we can list all environment variables.
  ![task1.1](docs/logbook4/task1_ph1.png)
  ![task1.2](docs/logbook4/task1_ph2.png)
  - Using export and unset we can set or unset envorinment variables.
  - In this screenshot we show how to set a environment variable **OURENV** to the value "G0808" using **export** and also how to unset it using the command **unset**
  ![task1.3](docs/logbook4/task1_ph3.png)

- **Task 2**:
  - First, we executed the code, printing the environment variables for the child proccess (childEnv).
  - Then we altered the code so it would print the environment variables for the parent process (parentEnv).
  - Finally, we compared them using the diff command and conclude that the son inherited the parent's environment variables. 

![task2](docs/logbook4/task2_ph1.png)

- **Task 3**:
  - First, we executed the code and nothing was printed.
  - Then we changed the last argument of execve() to *environ* and the environment variables were printed.
  - We can conclude that the environment variables need to be passed by the parameter *environ*.

![task3](docs/logbook4/task3_ph1.png)

- **Task 4**:
  - With the system() call all environment variables are passed to the new program /bin/sh.

![task4](docs/logbook4/task4_ph1.png)

- **Task 5**:
  - After compiling and setting this program as a SET-UID program we set the LD_LIBRARY_PATH and ANY_NAME environment variables to "something" and "else",respectively.
  - Since we are executing a program with root privileges in a user account some environment variables will not be exported. As we can see in the screenshot only the ANY_NAME environment variable was exported correctly to "else".
  - DESTACAR AS VARIAVEIS DE AMBIENTE INTERESSANTES NAS FOTOS

![task5.1](docs/logbook4/task5_ph1.png)
![task5.2](docs/logbook4/task5_ph2.png)
![task5.3](docs/logbook4/task5_ph3.png)
- **Task 6**:
  - 
  
