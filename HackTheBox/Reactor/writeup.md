# Reactor
<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/476fee19-485d-40f4-a5a4-a9990d88f31a" />

---

### Enumeration 

Let's Nmap(Fast Scan) it first :

<img width="520" height="161" alt="01_nmap_fast_scan" src="https://github.com/user-attachments/assets/8797e396-4324-4bb8-be74-e087206887a8" />

Two ports are open, namely : 22 and 3000, let's be more confirm and run a full scan in stealth mode :

<img width="635" height="178" alt="02_nmap_all_ports_stealth_scan" src="https://github.com/user-attachments/assets/18c26ae0-c399-416c-a863-ae7d83b5d3c6" />

Now, we can do a agrresive scan on the two ports : 22 and 3000, as shown below:

<img width="754" height="612" alt="03_nmap_aggressive_scan" src="https://github.com/user-attachments/assets/697681a4-343e-4648-8722-acb76982674e" />

We can now, firmly confirm that on port 22 we have ssh and on port 3000 we have a web page.
The dashboard is as shown below, with its version number marked :

<img width="1056" height="718" alt="dashboard" src="https://github.com/user-attachments/assets/ba6c64fb-01f5-42b6-b28e-6840870c4092" />

Now, we can move to the next step which is directory discovery, which was not that fruitful, as follows :

<img width="831" height="315" alt="gobuster_scan" src="https://github.com/user-attachments/assets/f2ea051d-4c55-4792-a6ba-668d8130a32f" />

Lets, see the web technologies used, which is as follows :

<img width="1060" height="67" alt="04_confirming_next_JS" src="https://github.com/user-attachments/assets/6e960a45-64ae-4919-8d5f-20a786e56f86" />

I have used the `whatweb` tool , and we are confirmed that next.JS is being used, so lets scan and test for React2Shell vulnerability.

<img width="570" height="256" alt="05_scanning_react2shell" src="https://github.com/user-attachments/assets/ac5c41f5-5a46-4491-832f-aa2c9bb54682" />

Now, its confirmed that the React2Shell, vulnerability is present, now let's exploit that vulnerability :

<img width="606" height="341" alt="react2shell" src="https://github.com/user-attachments/assets/56c99d06-d2c4-4c57-942c-24176e34928e" />

Now, our first job is to stabalize the shell.

<img width="650" height="184" alt="06_stabalizing_shell" src="https://github.com/user-attachments/assets/1499780e-80aa-4842-8a80-a34b772ead39" />

<img width="634" height="163" alt="08_stabalizing_shell" src="https://github.com/user-attachments/assets/6061ae2a-f63d-4d3f-8de7-80aee3f265d6" />


<img width="702" height="322" alt="09_stabalized_shell" src="https://github.com/user-attachments/assets/d0f38cff-9b8e-465e-ae82-f5cb66d0a0c5" />

now we got a stabalized shell, lets move on to our next part.

## Privilege Escalation 
