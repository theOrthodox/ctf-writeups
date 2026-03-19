# Natas Level 06
## Credentials
username : natas6
password : you need to solve the previous level for that
URL : http://natas6.natas.labs.overthewire.org/
## Aim
To find the password of the next level.
## Solve
The presents us the login form, asking username and password. As shown below :
<img width="496" height="298" alt="natas30" src="https://github.com/user-attachments/assets/2b1e8381-c9ef-4f0e-9e1e-581ea8f5a5b7" />
After login, we are presented with a new page, as shown below :
<img width="1488" height="266" alt="image" src="https://github.com/user-attachments/assets/f8556cc0-836e-47a5-b112-defa3a7c9f51" />
It asks for a secret, which on entering we guess will give us the password for the next level.
On understanding the sourcecode, we understand that there is directory named `includes/secrets.inc` which is being included in the logic to check the secret, the logic is shown below :
<img width="1068" height="561" alt="image" src="https://github.com/user-attachments/assets/4fb853f8-fe66-4961-90fd-0bc2c7c3c862" />
On visiting the directory, we find a blank page, as shown below :
<img width="1486" height="270" alt="image" src="https://github.com/user-attachments/assets/1b63f260-ebf9-45ce-b531-dce4ca1d7ea5" />
but on the source code , we find a secret as shown below :
<img width="863" height="182" alt="image" src="https://github.com/user-attachments/assets/95fe9ff1-708e-4ab5-9635-4c3c7f9a16d5" />
And on entering the same secret, we are able to retreive the password of the next level.
<img width="602" height="232" alt="image" src="https://github.com/user-attachments/assets/b02ecb17-6685-486e-a7c4-c6ca6eca1891" />
Hence, level complete !!!











