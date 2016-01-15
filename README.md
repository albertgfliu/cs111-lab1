# UCLA CS 111 Winter 2016 Lab 1a - Simpleton Shell

There are several things worth noting in our implementation of the simpsh, 1a:

1. We made an assumption that the amount of file descriptors opened would not exceed 1000.

2. We assume that the options of simpsh referring to the logical file descriptors 
do not know if these fds are operating or not prior to execution. Thus, we still 
maintained a logical fd number fd[] for each file. If the "open" fails, 
the logical fd can be mapped to a dummy value to signify invalid fd. 

3. The simpsh “command” option does not check if the file descriptor numbers are valid.

4. For the purpose of this lab 1a, we assume the user is advised of the correct format of the arguments following “command”. execvp() just takes whatever there and executes 
(which may fail or succeed).

5. We assume that without the “wait” option, it is possible that none of the 
child processes of the subshells will finish before simpsh finishes executing 
all of its options. We implemented the “command” option by obtaining the 
status of child process with WNOHANG without "actually waiting" for any process to terminate.

