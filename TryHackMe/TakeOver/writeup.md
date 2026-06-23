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
step 3 : cntrl + o + enter
step 4 : cntrl X
```
now we can simply go to that website and see its content, as shown below :
<img width="957" height="777" alt="image" src="https://github.com/user-attachments/assets/45c07a36-46d1-4f66-8fcb-bceca8ce3f0d" />



