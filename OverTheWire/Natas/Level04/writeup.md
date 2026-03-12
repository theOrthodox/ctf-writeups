# Natas Level 04
## Credentials 
username : natas4
password : solve the previous level to have the password
URL :      http://natas4.natas.labs.overthewire.org/
## Aim
## Solve
On visiting the URL, we get a login form , as shown below :
<img width="960" height="418" alt="natas17" src="https://github.com/user-attachments/assets/2ba217cf-0ef9-437c-b69d-b8ec99b33bc1" />
On entering the right, username and password. We get a page with a message, as shown below :
<img width="958" height="417" alt="image" src="https://github.com/user-attachments/assets/ad3014d6-f05d-4138-b78a-2435f41a9dc5" />
The message : `Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/" `.
The message hints us that, that the page is not authorized to those who are comming from : `http://natas4.natas.labs.overthewire.org/`, rather it expects us to visit the site from : `http://natas5.natas.labs.overthewire.org/`, but at this point it is not possible, because we donot have the access of that site.
So, we will take the help of BurpSuite, to examine further, and with the help of the statement. We will try to get the password.
### In Burp Suite :
We are examining to what happens when we are clicking the refresh button.
The following requests come to vision :
<img width="1799" height="641" alt="natas19" src="https://github.com/user-attachments/assets/85147be0-0f04-4147-8922-a0305819252d" />
The image above highlights that in the `Request`, that has a `Referer` header and is updated with the URL : `http://natas4.natas.labs.overthewire.org/`.
#### Understanding Referer Header 



