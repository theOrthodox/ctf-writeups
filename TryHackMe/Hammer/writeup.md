Platform: TryHackMe
Room: Hammer
Difficulty: Medium

# Task : 
1. What is the flag value after logging in to the dashboard?
2. What is the content of the file /home/ubuntu/flag.txt?

# Let's Solve :

### Nmap Scan
After getting the IP Address, let's NMAP it to find the services running and the ports opened. 
And the results are :
![NmapScan](images/nmap_hammer.png.png)

### Dashboard
We notice that, a port : 1337 is open and hosting webpage server. 
On viewing on the search engine we get a login dashboard as follows :
![DashBoard](images/dashboard.png)

### Source Code 
It is good practice to analyze the source code , before initiating to sub-domain enumeration, as sometimes we may get clue about the naming convention used by the developer of the directories and sub-domains.
The Source Code is shows as below :
![SourceCode](images/source_code_hammer_thm)
The source clearly states that the conventions for the sub-domains is : hmr_Directory_Name. Which means that , every dirctory listed will start with "hmr_".
So to enumerate the directories we need to first have the wordlist with the modification as required.
We will modify the word list : sed `'s/^/hmr/' words.txt > new_words.txt`.
Executing as follows :
![Modifying list](images/modifying_list)
So, its now we are ready with the word list to enumerate the directories.

### Enumerating Directories :
We will be enumerating the directories using the FeroxBuster, due to its fast nature and supports recurssive scanning.
After successful enumeration we get :
![Ferox Buster](images/FerroxOxide)
We were able to get two interesting directories as underlined in the above image. They are :
1. hmr_logs
2. errors.logs
The significance of these two is quite unavoidable, because in the login form we donot have any known email address that we can use to break the login page. The plan should be to get any email address so that we can us the forgot password option, and as a good news we get an email address as shown below :
Interface of "\hmr_logs":
![hmr_logs](images/hmr_logs)

What we get inside "errors.log" : (its interesting)
![hmr_errors](images/hmr_errors)

Now , we have an email address : tester@hammer.thm.
We will be using it for the Authentication Bypass.

### Authentication Bypass
We first need to analyze the login form (mostly the forgot password), we then be able to get an idea about how the password reset works.
The Forgot Password page looks somethng like this :
![Forgot Password](images/forgot_hammer.png)
On entering 


















