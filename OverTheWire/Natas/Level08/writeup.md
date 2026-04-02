# Natas Level 08
## Credentials 
username : natas8
URL : http://natas8.natas.labs.overthewire.org/
## Aim
to get the password of the next level.
## Solve 
On entering the url , we are asked to enter the username and password, as shown below :

<img width="547" height="371" alt="image" src="https://github.com/user-attachments/assets/ec5d9c8f-840c-4ae6-bfff-9996a570276c" />

On entering the correct, username and password we can access the webpage, as shown below :

<img width="958" height="300" alt="image" src="https://github.com/user-attachments/assets/d0d35409-43e7-4755-afa5-f3273ca58790" />

We are required to enter a secret code, which can give us the password for the next level.
We then tried to understand the source code , as shown below :

<img width="904" height="627" alt="image" src="https://github.com/user-attachments/assets/ca66dad6-4934-4e74-8a64-1cfbd84d5737" />

We can clearly see the logic of the function : 
```
function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}
```
The function takes secret as a parameter, then does the encoding in the order : 
`base64 encode -> reverse -> hexa decimal`.
So , we have the returned value of the function encode as : `3d3d516343746d4d6d6c315669563362`
We just to reverse the order to decode the secret, and the order for that is :
`hexadecimal -> string -> reverse -> base64 decode` as shown below : 
<img width="576" height="257" alt="image" src="https://github.com/user-attachments/assets/75a7fbd6-410c-4ecb-bdb7-d7bfd24ac9a6" />

Now, we gave the secret as the input and guess what, we recieved the password!!.
<img width="955" height="402" alt="image" src="https://github.com/user-attachments/assets/4fc7d708-a8f1-4070-81c4-c267fa74cc8c" />

Hence, level completed !!!
