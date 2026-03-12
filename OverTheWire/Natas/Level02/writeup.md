# Natas Level 02
## Credentials
Username: natas2

Password: to get the password check out the tutorial of the previous level.

URL: http://natas2.natas.labs.overthewire.org

## Aim
To find the password of the next level

## Solve
After the successful login, using the password retrieved from the previous level.
<img width="963" height="351" alt="image" src="https://github.com/user-attachments/assets/85ed768a-9f20-42cd-9447-e836331c427e" />
The message cleary says that, there is nothing on the current page. So, we need to crawl around to see if we have any directory, that would suggest us the password of the next level.
There we found a directory in the source code.As shown below:
<img width="963" height="396" alt="natas10" src="https://github.com/user-attachments/assets/41c3154e-6c79-4178-ad7d-3722b8c50551" />
We moved to the new directory found to find the contents of it.
As shown below :
<img width="959" height="343" alt="image" src="https://github.com/user-attachments/assets/da832a48-4171-4337-a9c0-26b19f84791b" />
Here, we have an interesting file named : `users.txt`.
On opening the file, we get usernames and password of various other users.
<img width="957" height="305" alt="image" src="https://github.com/user-attachments/assets/2abcf9c8-2f62-4825-880b-d4cd1c692882" />
Hence, we found the password for the next level. 
The level is complete!!!




