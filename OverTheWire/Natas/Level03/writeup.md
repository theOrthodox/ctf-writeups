# Natas Level 03
## Aim 
To find the password of the next level.
## Solve
On opening the URL provided, we get the login page as follows :
<img width="955" height="387" alt="image" src="https://github.com/user-attachments/assets/5de4d214-0055-439a-98b0-477494e1f301" />
On entering the right username and password, a page open opens as follows :
<img width="960" height="315" alt="image" src="https://github.com/user-attachments/assets/a7e55fd3-7c62-413a-aea7-afd384c3992a" />
Which states that `There is nothing on this page.`
We also tried to read the source code as follows :
<img width="951" height="366" alt="natas16" src="https://github.com/user-attachments/assets/1553d894-3089-4f35-b10b-7d32d3628273" />
there we get a message which states that :
`<!-- No more information leaks!! Not even Google will find it this time... -->`
So, our next place to move is `robots.txt`.
`robots.txt` file is used to tell web crwalers (bots) which parts of a website they are allowed to access.It is manily used for search engine indexing control.
The `robots.txt` contents are as follows :
<img width="953" height="171" alt="image" src="https://github.com/user-attachments/assets/911ecde8-a576-442d-9c87-079b19c967e5" />
Here, we found a directory : `/s3cr3t`
On moving to the directory , we found what we were looking for :
<img width="953" height="355" alt="image" src="https://github.com/user-attachments/assets/78556b8e-e92b-47d1-a239-5603e2b87e62" />
The `users.txt` appears, the contents of this file has the password of the next level.
<img width="956" height="140" alt="natas15" src="https://github.com/user-attachments/assets/d23affb5-3919-466b-a089-2da7cb103fa0" />
Hence, we got the password.
Level Complete!!!






