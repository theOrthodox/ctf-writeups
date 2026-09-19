# Orion

<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/3699dcfd-5ec5-4b94-88b5-ca27abae0e61" />

---

### Task 1
How many open TCP ports are listening on Orion?

`2`

<img width="543" height="137" alt="01_nmap_fast_scan" src="https://github.com/user-attachments/assets/037861eb-eeca-4352-9ccb-899857ffe9d4" />

<img width="782" height="270" alt="02_nmap_aggressive_scan" src="https://github.com/user-attachments/assets/8ebbea63-e237-407b-8747-4d6c2d26e09a" />

---
### Task 2
What is the version of CraftCMS running on the target?

`5.6.16`

<img width="1334" height="62" alt="03_whatweb" src="https://github.com/user-attachments/assets/d6e41c4c-9a03-46fc-be03-025ba36a4ecf" />

<img width="688" height="415" alt="04_dir_scan" src="https://github.com/user-attachments/assets/2acfcd88-14f2-4078-8e17-9273d2258932" />

<img width="765" height="669" alt="05_cms_versions" src="https://github.com/user-attachments/assets/d61ce74c-74fc-4059-9782-e546a691eb8a" />


---
### Task 3
Which user is running CraftCMS?

`www-data`

To get to the user who is running the CraftCMS, we need to get the shell for it. 
The Version of the CraftCMS is vulnerable and a CVE is available, but all the POC available is not working, so we took the help of `Mestaploiit`, each step is shown below with a valid POC.

<img width="775" height="321" alt="06_msf_01" src="https://github.com/user-attachments/assets/6d7653b6-7dc6-4f84-b827-5f2bce4dd241" />

First, we will search out the technologies name in the msf-console, and we got the exploit.

<img width="894" height="645" alt="image" src="https://github.com/user-attachments/assets/0064e660-e582-4dbf-a9f0-65c6c06cae88" />

Now, we will view its options, and set accordingly as show above.
RHOSTS means the Target's URL and the LHOST is the attackers IP address.

<img width="585" height="310" alt="image" src="https://github.com/user-attachments/assets/9ee81442-08f5-49ba-8d8c-cbac4758f99c" />

In the last step we will use the command `exploit`, and we can see the an active sessions. We need to stabalize it a bit as shown above. 
There we get out user.


---
### Task 4
Which file contains the password for the MySQL database?

`.env`

<img width="560" height="533" alt="09_msf_mysql_password_04" src="https://github.com/user-attachments/assets/b727c3d6-4eb9-41bc-a182-b3846ad22401" />


---
### Task 5
What is the password that can be obtained from the MySQL database?

```darkangel```

<img width="527" height="226" alt="10_mysql_login_01" src="https://github.com/user-attachments/assets/875941d1-1d11-4be6-b644-a6916bd7a757" />

<img width="632" height="629" alt="11_mysql_use_database_02" src="https://github.com/user-attachments/assets/386cb914-fa01-4163-9988-a7e506b3e72e" />

<img width="1330" height="215" alt="12_mysql_hash_03" src="https://github.com/user-attachments/assets/83d8d3f5-7e4a-479e-bf83-585324d722e0" />

<img width="756" height="166" alt="13_hash_cracked" src="https://github.com/user-attachments/assets/6e1ea02a-61f8-4142-be9d-be2e57608d59" />


---
### Submit User Flag
Submit the flag located in the Adam user's home directory.

User flag owned

<img width="962" height="581" alt="14_ssh_login" src="https://github.com/user-attachments/assets/b43c32b3-24bd-4fd9-90ed-b04d7a243710" />

<img width="326" height="60" alt="user txt" src="https://github.com/user-attachments/assets/d389bb55-d40d-4443-b397-90af49e292c9" />


---
### Task 7
Which service, unrelated to CraftCMS, is open only locally on Orion?

`telnet`

<img width="1233" height="142" alt="15_telnet" src="https://github.com/user-attachments/assets/e2cd33ba-f647-4ac8-b4e4-be556bc480ad" />


---
### Task 8
What is the version of the service found?

`2.7`

<img width="658" height="110" alt="16_telnet_version" src="https://github.com/user-attachments/assets/02bb8efc-1e6e-4d23-b5ba-64001ec0a521" />


---
### Submit Root Flag
Submit the flag located in the root user's home directory.

<img width="1020" height="589" alt="root txt" src="https://github.com/user-attachments/assets/8f0c9358-bc5a-4195-b858-0c9379e4e6c0" />

Reference : https://github.com/0xBlackash/CVE-2026-24061 
---


<img width="517" height="304" alt="congo" src="https://github.com/user-attachments/assets/4e6fabef-9d7a-45d5-a1d0-36e037e65104" />

---
Thank You!!!

