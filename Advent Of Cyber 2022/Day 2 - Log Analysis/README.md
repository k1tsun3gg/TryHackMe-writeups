## The Story

Santa’s Security Operations Center (SSOC) has noticed one of their web servers, santagift.shop has been hijacked by the Bandit Yeti APT group. Elf McBlue’s task is to analyse the log files captured from the web server to understand what is happening and track down the Bandit Yeti APT grou

## Learning Objectives
In today's task we will learn:
- Learn what log files are and why they're useful
- Understand what valueable information log files can contain
- Understand some common locations these log files can be found
- Use some basic linux commands to start analysing log files for valueable information
- Help Elf Mcblue track down the Bandit Yeti APT

## Tasks

### Task 1: Ensure you are connected to the deployable machine in this task.
``` No answer needed ```
### Task 2: Use the ls command to list the files present in the current directory. How many log files are present?
``` We can see there is 2 log files present SSHD.log and webserver.log```
### Task 3: Elf McSkidy managed to capture the logs generated by the web server. What is the name of this file?
```webserver.log```
### Task 4: Begin investigating the log file from question #3 to answer the following questions.
``` No answer needed```
### Task 5: On what day was Santa's naughty and nice list stolen?
We can use the following command: ```cat webserver.log``` to see that the logs are from the 18th of November, if we look at our calendar we can see this was on a **Friday**
### Task 6: What is the IP address of the attacker?
We can see in the logs the requests are coming from only one ip ```10.10.249.191```
![ip](https://user-images.githubusercontent.com/84150540/207566495-c37dff4f-0991-4e34-85c3-3cd8653e00b1.png)

### Task 7: What is the name of the important list that the attacker stole from Santa?
So here we have to find the filename of the list that got stolen we can use grep for this and look for the .txt file extension.

```cat webserver.log | grep "\.txt" ```
![image](https://user-images.githubusercontent.com/84150540/207569496-b5098afd-2426-4035-944b-9804284f8784.png)

we can see it is ```santaslist.txt``` that got stolen.


### Task 8: Look through the log files for the flag. The format of the flag is: THM{}

For this question we can again use grep but this time we specify the ``` -r ``` switch to recursively search.
```bash cat webserver.log | grep -r "THM{" ```
and we can see we get the flag.

![flagday2](https://user-images.githubusercontent.com/84150540/207570528-c2fed3df-d7ac-4e70-a1eb-a9b4aaaafdf1.png)
