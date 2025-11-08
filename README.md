# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```c

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```














## OUTPUT


<img width="476" height="388" alt="image" src="https://github.com/user-attachments/assets/0482ee27-fabd-4efc-8a8e-16d72388e89f" />













## C Program to create new process using Linux API system calls fork() and exit()
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}


```










## OUTPUT


<img width="296" height="203" alt="image" src="https://github.com/user-attachments/assets/43129808-4f69-4e86-9934-5686deafd878" />






## C Program to execute Linux system commands using Linux API system calls exec() family
```c

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```





















## OUTPUT

<img width="584" height="815" alt="image" src="https://github.com/user-attachments/assets/1f62631e-ad85-4818-b0d2-cbe889ff97ce" />


<img width="1149" height="822" alt="image" src="https://github.com/user-attachments/assets/a742a01d-d630-4e3b-af53-789708747448" />

<img width="1898" height="846" alt="image" src="https://github.com/user-attachments/assets/31496b20-6b8f-488c-a561-38735c6d3296" />

<img width="659" height="796" alt="image" src="https://github.com/user-attachments/assets/a46baf16-f252-42de-96c7-ff494313ab33" />










# RESULT:
The programs are executed successfully.
