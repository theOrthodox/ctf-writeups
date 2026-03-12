# Natas Level 05
## Credentials
username : natas5
password : You have to solve the previous level 
URL : http://natas5.natas.labs.overthewire.org/
## Aim
To get the password of the next level.
## Solve
On visiting the URL, we get a login form.As shown below :
<img width="1527" height="423" alt="natas22" src="https://github.com/user-attachments/assets/2e1e82b4-7f4c-486c-97a0-7af9c1d198c7" />
On entering a valid username and password, we get a web page with the following message :
<img width="1804" height="325" alt="natas23" src="https://github.com/user-attachments/assets/90a6bef8-2c72-429a-96fb-2da29abc5734" />
The message clearyl says that : `Access disallowed. You are not logged in`.
So, taking it as hint,lets inspect using Burp Suite. We can also inspect using the developers tools, but Burp Suite makes it more convenient.
On viewing the `Request` of the page which shows the message we found :
<img width="1185" height="479" alt="image" src="https://github.com/user-attachments/assets/3be5b0af-f439-4a96-ae87-7a3fc2e730c1" />
With the help of the interceptor, we refreshed the page to see what is the `GET REQUEST`.
<img width="442" height="318" alt="natas24" src="https://github.com/user-attachments/assets/91330818-6ee8-4850-8ad0-7405e1bbbdd3" />
There is a cookie, named : `loggedin`.Whose parameter is set to be `0`.
Now, it is the mechanism used by the developer to restrict us from the password of the next level.
But, we can bypass it by simply changing it to `1`, as shown below :
<img width="1241" height="671" alt="image" src="https://github.com/user-attachments/assets/14e3eac9-fff5-419b-9546-986bb29cf643" />
Hence, we were successful in geting the password for the next level.
<img width="938" height="255" alt="natas28" src="https://github.com/user-attachments/assets/f6638ed5-1996-49b4-9743-0ad710408623" />
Level completed !!!
