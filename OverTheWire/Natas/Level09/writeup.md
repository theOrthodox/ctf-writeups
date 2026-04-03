# Natas Level 09
## Credentials 
username : natas9
URL : http://natas9.natas.labs.overthewire.org/
## Aim
to get the password of the next level.
## Solve 
On entering the url , we are asked to enter the username and password, as shown below :

<img width="744" height="352" alt="image" src="https://github.com/user-attachments/assets/23b3afc8-2489-4695-8f07-c8ef205a99db" />

On correct credentials we get a web page as shown below :

<img width="959" height="321" alt="image" src="https://github.com/user-attachments/assets/8cb3f229-6e12-4661-844d-efa17e1ca02c" />

Now lets analyze the source code : 

<img width="955" height="591" alt="Screenshot 2026-04-03 000236" src="https://github.com/user-attachments/assets/a3933ae2-f629-420e-9d12-8f14a44314df" />

The logic :
```
if(array_key_exists("needle,$_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
```
The logic here, is that :

**
The code first checks whether the user has sent a parameter named "needle" using the $_REQUEST superglobal.
If it exists, its value is stored in the variable $key.
Then it checks whether $key is not empty.
If it is not empty, the passthru() function executes a Linux shell command (grep -i) using the user input and prints the output from dictionary.txt.
The vulnerability is that the user input ($key) is directly inserted into the shell command without any sanitization, which can lead to command injection.
**
Now we will exploit this vulnerability, as shown below : (we know that from level 07 that in "natas/wep_pass/natas<level>" , stores the password for the level)
We used the command `;cat natas/web_pass/natas10`, and we get the password as shown below :

<img width="959" height="603" alt="Screenshot 2026-04-03 002119" src="https://github.com/user-attachments/assets/4217d07f-7dc2-4ace-9468-fa35460fad18" />

hence level completed!!!
