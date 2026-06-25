# TakeOver
<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/cda6c686-c047-4cf8-bea3-3a8b199475ed" />

This challenge revolves around subdomain enumeration.
---
## Task 1 
```
Hello there,

I am the CEO and one of the co-founders of futurevera.thm. In Futurevera, we believe that the future is in space. We do a lot of space research and write blogs about it. We used to help students with space questions, but we are rebuilding our support.
Recently blackhat hackers approached us saying they could takeover and are asking us for a big ransom. Please help us to find what they can takeover.
Our website is located at https://futurevera.thm(opens in new tab)
Hint: Don't forget to add the <MACHINE IP> in /etc/hosts for futurevera.thm ; )
```

---
solution :
lets first follow the instructions given and add ip and the domain name to our `etc/hosts`.
```
step 1 : sudo nano etc/hosts
step 2 : enter <machine ip>  futurevera.thm
step 3 : ctrl + o + enter
step 4 : ctrl X
```
now we can simply go to that website and see its content, as shown below :

<img width="957" height="777" alt="image" src="https://github.com/user-attachments/assets/45c07a36-46d1-4f66-8fcb-bceca8ce3f0d" />

Then as a routine habbit we did nmap and the result is as follows :

<img width="647" height="222" alt="image" src="https://github.com/user-attachments/assets/875c700c-53de-480f-849e-826b3a13d6a4" />

As the room name and descriptions hints us that its a ```sub-domain enumuration```.
So, there is nothing to focus from the nmap results.
Lets, do the sub-enum with ```ffuf```tool, as follows:

<img width="957" height="827" alt="image" src="https://github.com/user-attachments/assets/8d2c8042-221e-41b1-b87f-ee0916fd249c" />

but with this we will not get any conclusion, so we need a filteration which we will do with respect to lines.
So our next command will be:
``` ffuf -H "host:FUZZ.<domain>" -u <url> -w <wordlist path> -fl <filtering_length>```, 
```
Option	                 Description
ffuf	                   Fuzz Faster U Fool, a web fuzzing and enumeration tool.
-H "Host:FUZZ.<domain>"	 Adds a custom Host header. FUZZ is replaced with words from the wordlist to discover hidden virtual hosts.
-u <url>	               Target URL or IP address where requests are sent.
-w <wordlist_path>	     Path to the wordlist used for fuzzing. Each word replaces FUZZ.
-fl <filtering_length>	 Filters responses with the specified line count, helping remove false positives and default responses.
```
implementation is as follows : 

<img width="961" height="557" alt="image" src="https://github.com/user-attachments/assets/166113e8-22a9-4b78-ae34-79ade2f07807" />

we got two sub-domains namely : 
1. blog
2. support
   
lets explore these sub-domains, but before exploring lets first add it our ```etc\hosts\``` with the subdomains, as shown below :

<img width="832" height="222" alt="image" src="https://github.com/user-attachments/assets/4c18f649-1ef1-44ec-8840-f29d724bec05" />

now, we ready to explore !!
first, lets go with ```blog```. The url : ```https://blog.futurevera.com```, opens up with a warning as shown below :

<img width="952" height="700" alt="image" src="https://github.com/user-attachments/assets/59fbd992-5aba-4d86-b2fe-bb05024b627a" />

and the certificate shows no interesting thing :

<img width="336" height="647" alt="image" src="https://github.com/user-attachments/assets/9b8e3c18-a211-41ae-b0c0-3e781849cf94" />

 and we have, three directories only :
 1. about
 2. home
 3. post
with no point in further deep diving lets also explore another sub-domain : ```support```
Again, we saw the same warning, as shown below :

<img width="952" height="672" alt="image" src="https://github.com/user-attachments/assets/ab9648d9-c73e-4440-94a6-bc587c58ea94" />

but in the certificate, we found something interesting :

<img width="341" height="650" alt="image" src="https://github.com/user-attachments/assets/8665de95-62a8-4c95-b7f8-51c398b9b120" />

a doman name : ```secrethelpdesk934752.support.futurevera.thm```
lets update it to ```etc\hosts\```, and again we can see a warning page as shown below with a flag in that :

<img width="957" height="816" alt="image" src="https://github.com/user-attachments/assets/62948345-3321-4ed6-a793-86ac01c4e956" />

note: the above flag is availabe in ```http``` and not ```https```.

and hence we completed this challenge!!!

<img width="737" height="255" alt="image" src="https://github.com/user-attachments/assets/cc61a67d-3f33-4722-9d91-e27d9ed840e7" />









