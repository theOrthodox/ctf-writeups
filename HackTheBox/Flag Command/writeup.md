# Flag Command
Easy | Web
---
<img width="142" height="142" alt="image" src="https://github.com/user-attachments/assets/e9ac5687-4ee7-424d-acde-00fd3f894077" />

---
## Challenge Scenario

Embark on the "Dimensional Escape Quest" where you wake up in a mysterious forest maze that's not quite of this world. Navigate singing squirrels, mischievous nymphs, and grumpy wizards in a whimsical labyrinth that may lead to otherworldly surprises. Will you conquer the enchanted maze or find yourself lost in a different dimension of magical challenges? The journey unfolds in this mystical escape!

---
## Solution

The web page opens to be CLI based, as shown below :

<img width="962" height="621" alt="image" src="https://github.com/user-attachments/assets/6f2a834e-9de9-4367-9340-d88ba717e8a1" />

So, we need to understand the game logic, and with a better reconn.. We can do better exploit.
Lets first do the routine :
1. robots.txt : not present
2. sitemap.xml : not present

lets, review the source code to find something intresting :

<img width="742" height="525" alt="image" src="https://github.com/user-attachments/assets/8bd4f998-5a3c-4576-b44d-3683e0d5341a" />

we found some reference and the interesting ones are follows :

1. "/static/terminal/.js/command.js"
   <img width="727" height="492" alt="image" src="https://github.com/user-attachments/assets/b324ee99-43b6-4606-9910-bff97f8ab446" />
2. "/static/terminal/.js/main.js"
   <img width="748" height="613" alt="image" src="https://github.com/user-attachments/assets/7c60cfb0-47ed-4e91-abb2-cb26c9aa61a8" />
3. "/static/terminal/.js/game.js"
<img width="342" height="311" alt="image" src="https://github.com/user-attachments/assets/053b9464-e168-4366-9ad4-9ab05211266f" />

on image 2, I have highlighted a condition (condition shown below) :
```
if (availableOptions[currentStep].includes(currentCommand) || availableOptions['secret'].includes(currentCommand))
```

This condition says either the current step has a command or it should have a secret. 

We need to find the secret, I explored it and got a secret in the Developers tool -> Networks, as shown below :

<img width="740" height="330" alt="image" src="https://github.com/user-attachments/assets/a82d7c51-e1bc-4b36-9d03-9b81538c3428" />

Now, lets paste this secret, and lets see how the server interacts.
And we got the Flag!!! 

<img width="742" height="567" alt="image" src="https://github.com/user-attachments/assets/c0534961-033c-4c8b-8e5b-211fce171b3d" />

Hence, challenge completed !!
---
<img width="767" height="392" alt="image" src="https://github.com/user-attachments/assets/836e85e7-2026-488d-8476-a6cfff1b6c9f" />
---



