# Cohort
<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/4904624f-0f35-4091-88e9-a1ff84de701d" />

---

Firstly, Nmap Scan should be done in order to understand the ports:

1. Fast Scan :
   
<img width="522" height="154" alt="01_nmap_fast_scan" src="https://github.com/user-attachments/assets/72d7dca7-e4d8-4f17-97f1-8936f3d3ad72" />
   
3. All Ports Scan :
   
   <img width="526" height="148" alt="02_nmap_all_port_scan" src="https://github.com/user-attachments/assets/98de0b90-f5ab-4522-8800-ddff46312fca" />

5. Aggressive Scan :

   <img width="761" height="446" alt="03_nmap_aggressive_scan_on_ports" src="https://github.com/user-attachments/assets/c1bca053-e117-4e85-ac77-172f265d9d3f" />

Now, lets add it to our `/etc/hosts` file, 

<img width="514" height="484" alt="04_adding_to_etc_hosts" src="https://github.com/user-attachments/assets/74699020-1c90-407b-808d-60ceb63d6d0c" />

The next step of enumeration is see what is the webpage we get, as shown below :

<img width="957" height="688" alt="05_dashboard" src="https://github.com/user-attachments/assets/e1258cf6-3362-442d-bb31-47273cfdc4d3" />

Alongside that, lets run a directory scan with `Ferroxbuster` and the scan results are as follows :

<img width="1097" height="446" alt="13_ferroxbuster_scan" src="https://github.com/user-attachments/assets/1ec82e28-afbb-468a-b015-6410a8d0c30e" />

Im the webpage, we get an interesting endpiont, which results in SSRF and connects us to internal local hosts, as shown below :

<img width="994" height="667" alt="ssrf_endpoints" src="https://github.com/user-attachments/assets/565db76e-f6b9-4aad-b9d2-47c740e30f5d" />

We captured the request in `BurpSuite` and we tried to bypass the filter as shown below :

<img width="1036" height="619" alt="06_internal_ip_01" src="https://github.com/user-attachments/assets/c8031d98-0b5f-4d81-999a-88b39c8075d7" />

<img width="1034" height="477" alt="07_internal_ip_02" src="https://github.com/user-attachments/assets/1a6377ae-a6ca-4a10-88d7-caa3cd0d21a5" />

As we have bypassed the filter with `127.1`, now we can proceed with the further enumeration.
We tried to retrieve those endpoints, which had a redirection or was not authorized for a normal user to view, so as an internal ip address, we can see those endpoints as shown below :

<img width="952" height="290" alt="08_internal_ip_dir_01" src="https://github.com/user-attachments/assets/f8c1de5c-b1ff-4f2b-be07-9845ca814a5a" />

<img width="988" height="310" alt="09_internal_ip_dir_02" src="https://github.com/user-attachments/assets/0c4a2a01-8911-465f-977a-da7ccce6e5e5" />

<img width="1075" height="326" alt="10_internal_ip_dir_03" src="https://github.com/user-attachments/assets/59ce447a-1311-4bfe-a8b8-d1d44647cdbe" />


here we get a vritual host, which is marked in the poc, as shown below :

<img width="1071" height="268" alt="11_internal_ip_dir_04" src="https://github.com/user-attachments/assets/cd32fbbc-e016-48aa-8f87-6b9effd2894d" />

We need to add those in our `/etc/hosts/` file in order to access the webpage, and we get :

<img width="990" height="703" alt="12_marimo_dashboard" src="https://github.com/user-attachments/assets/0af0bf53-36a0-48bd-84b5-ec4a232eb7e3" />

We get an interesting thing called `Marimo`, lets understand it :

`
CVE-2026-39987 is a critical pre-authentication remote code execution vulnerability in Marimo versions before 0.23.0. The `/terminal/ws` WebSocket endpoint lacked proper authentication, 
allowing unauthenticated attackers to establish a terminal connection and execute arbitrary commands on the affected server. Successful exploitation could provide a remote shell with the privileges of the Marimo process.
`

in simple terms :


Imagine a building with a security desk. Normally, you must show your ID before entering. But in vulnerable Marimo, there was a back door (the /terminal/ws endpoint) where the security guard wasn't checking IDs.
So an attacker could enter without authentication, open a terminal, and run commands on the server.

---> Normal → Login → Terminal → Commands


---> Vulnerable → Terminal directly → Commands → Remote Code Execution

For the exploitation part, we used a git repositroy 
https://github.com/M3PH1569/CVE-2026-39987-POC/blob/main/CVE-2026-39987.py

Its implementation is as follows :

<img width="1037" height="522" alt="user txt" src="https://github.com/user-attachments/assets/a9f22114-cb9e-43f4-a782-2c7d3a119577" />

and there we get our `user.txt`.

Now, lets move to other part.

<img width="1090" height="154" alt="14_git_package" src="https://github.com/user-attachments/assets/760a9b09-0263-4b05-9d4f-03d9b1f4aecb" />

we got something interesting, and hows it let me explain :

`PackageKit can become a privilege-escalation vector because it runs certain package-management operations with root privileges. If an installed version contains a vulnerability, 
a low-privileged user may exploit it to make PackageKit perform unauthorized actions as root, potentially gaining a root shell.`

The version of the PackageKit is vulnerable, and can be exploited.
With the help of the git repository :
https://github.com/0xBlackash/CVE-2026-41651/blob/main/CVE-2026-41651.py

Lets, exploit it :

<img width="622" height="547" alt="root_txt" src="https://github.com/user-attachments/assets/b4289429-2e08-4e98-833c-649d1cff3aea" />

and there we get our `root.txt`

---

<img width="608" height="310" alt="z_congo" src="https://github.com/user-attachments/assets/d8be86d8-4c59-4de3-a995-3cdb7b5b58d1" />

---
Thank You!!!









