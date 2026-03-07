Platform: TryHackMe
Room: Hammer
Difficulty: Medium

Task : 
1. What is the flag value after logging in to the dashboard?
2. What is the content of the file /home/ubuntu/flag.txt?

Let's Solve :

After getting the IP Address, let's NMAP it to find the services running and the ports opened. 
And the results are :
</> Markdown
## Nmap Scan
![Nmap Scan](images/nmap.png)
We notice that, a port : 1337 is open and hosting webpage server. 
On viewing on the search engine we get a login dashboard as follows :

## Dashboard 
<\> Markdown
![DashBoard](images/dashboard.png)







