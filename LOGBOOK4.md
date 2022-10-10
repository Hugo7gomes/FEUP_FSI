# Tasks for week \#4

- **Task 1**:
![task1.1](docs/logbook4/task1_ph1.png)
![task1.2](docs/logbook4/task1_ph2.png)
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
  - Only the PATH and ANY_NAME variables set in the shell process got into the Set-UID child process. That didn't happen with the LD_LIBRARY variable.

![task5.1](docs/logbook4/task5_ph1.png)
![task5.2](docs/logbook4/task5_ph2.png)
![task5.3](docs/logbook4/task5_ph3.png)
- **Task 6**:
  - Only the PATH and ANY_NAME variables set in the shell process got into the Set-UID child process. That didn't happen with the LD_LIBRARY variable.
  
