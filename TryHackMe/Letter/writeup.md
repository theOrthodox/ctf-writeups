<img width="400" height="500" alt="image" src="https://github.com/user-attachments/assets/1badcc97-e0da-47be-9d29-6bfd5f0a1bfb" />

# Letter
Can you help us find out more about this letter?                                                            
Easy | [Room](https://tryhackme.com/room/letter)
---
### Background Scenario 
It's just another Monday morning on your mail delivery route when an unusual letter catches your eye. The envelope is battered, riddled with holes as if it's been through a storm. The address is barely legible, and your coworkers at the post office wave it off as a lost cause.

But something about it nags at you.

You carefully open the damp envelope. Inside, you find a faded newspaper clipping and a short handwritten note. The clipping is torn and water-damaged, with key sections missing. The note is personal, clearly not meant for your eyes, but the fragments you can read hint at a story buried in time.

### Objective
 Use the clues provided in the zip file to uncover the full name and age of the person mentioned in the note.

 ### Flag Format 
 Flag format: THM{Name_Surname_age}, only the first letter of the name and surname should be capitalised

 ### Questions 
 1. What is the postal code of the delivery address on the envelope?
 2. What is the flag?

### Solution
We first need to extract the zip file provided and veiw its content.
The zip file contains 3 files. 
1. a png file
2. a text file
3. a png file

The contents of each file is listed below :
<img width="1448" height="1086" alt="letter" src="https://github.com/user-attachments/assets/23f38ba2-28e8-406f-b353-939028155266" />
`figure representing the Letter.png`
<img width="1021" height="397" alt="Newspaper_clipping" src="https://github.com/user-attachments/assets/a2d92c3c-8ba5-49c0-a1d6-4ee1acfa81e6" />
`figure representing Newspaper_clipping.png`
```
Mon cher Édouard,

Aujourd'hui, en rangeant le grenier chez mes grands-parents, je suis tombée sur cette vieille coupure de journal. Ton arrière-grand-père n'avait même pas l'âge de passer le permis quand il s'est distingué ce jour-là. Le benjamin de l'équipe, et certainement pas le moins courageux.

Il serait si fier de te voir sur l'eau à ton tour.

Avec toute mon affection,
Audette
```
`text document `

Now, 1st we need to gather as much as information we can gather. Which will help us to connect the dots and answer the questions.
Lets first translate the text document in english :
```
English translation:

“My dear Édouard,

Today, while tidying the attic at my grandparents’ house,
I came across this old newspaper clipping.
Your great-grandfather wasn’t even old enough to get his driver’s license
when he distinguished himself that day—the youngest member of the team,
and certainly not the least courageous.

He would be so proud to see you out on the water in your turn.

With all my affection,
Audette”
```
There are few things to note from the text above :
1. reciever's first name :  **Édouard**
2. sender's first name : **Audette**
3. the reciever's grandfather had done something heroic, at a very young age, and he was the **youngest member** in his team.
4. The language of the text is French.

Now lets move to newspaper cutting. The image is quite blury but the name of the newspaper and its headings is readable. So to sum up the findings :
Name of the Newspaper : `L'Ouest-Eclair`
Headline : ***“M Herriot se déclare solidaire de M Painlevé”***
We can use this information to get the digital version of the newspaper for better readability.
There is a website named [gallica.bnf](https://gallica.bnf.fr/accueil/en/html/accueil-en), is the online digital library of the Bibliothèque nationale de France (BnF).  It is a massive archive where we can access historical and cultural documents for free.
There I found the newspaper in a better readable format : [redable newspaper](https://gallica.bnf.fr/ark:/12148/bpt6k5848808/f1.item.r=%22M%20Herriot%20se%20DECLARE%20SOLIDAIRE%20DE%20M%20PAINLEVE%22#)

Now, we can clearly see a lot of information in front of us :
1. date of the newspaper : 24 May 1925
2. The headline that matches with the note provided earlier :
   ```
   in French :
   “Une catastrophe sur les côtes du Finistère” translates to:
   Translated version :
   “A disaster on the coast of Finistère.”
   ```
From the above points its very much clear that the incident happened at the coast of Finistère.
So, now our next target should be where is Finistère.
```
Finistère is a coastal department in northwestern France,
located in the region of Brittany (called Bretagne in French).
```
We have discovered the department, and its `Finistère`, whose postal codes starts with 29. To be more accurate we need to find the town. There are total of : 277 towns/communes in Finistère.
Lets dig more to get any clue.
The sub heading says somethig more : 
```
in French :
Deux Bateaux De Peche en Perdition Et Deux canots de sauvetage sombrent au large de penmarch

translation :
“Two fishing boats in distress and two lifeboats sink off the coast of Penmarch.”

```
We got a new place : `Penmarch`, which is indeed a commune n Finistère, located in the region of Brittany.
It’s a coastal commune, known for its lighthouse, Phare d'Eckmühl, and its fishing heritage. 
And now, lets move to envelope.
The stamp says : `La Poste` 
And the reciever's first name is : `Edouard`.

We see an initialism : `SNSM` , whoes full form is :
`SNSM` stands for `Société Nationale de Sauvetage en Mer`.

In English, it means `“National Society for Sea Rescue.”`
It’s a French volunteer organization responsible for:
rescuing people at sea
assisting ships in distress
providing coastal safety and lifeguard services

So its very much clear that, the reciever is a volunteer in `SNSM`.
Now, its very much clear now that the person named ` Édouard` is a volunteer in a rescue team named `SNSM`, and is now posted in the coastal areas thats why the whole letter is wet by now, the note mention that his grandfather was a part of a rescue team in Penmarch in Finistère, France.
So its very much likely that his grandson is at the same town.

We hit the first question,
#### The postal code for Penmarch in Finistère, France is:
**29760**
---
Now, the next question asks us to find out the name of the great grandfather of the reciever.
We have pretty hints on him.
1. date of incident : 23 May 1925
2. date of reporting : 24 May 1925
3. Place : Penmarch in Finistère, France
4. a descriptive identifier within a group : youngest member

So with the above information I google Dorked, I found something interesting :

<img width="1044" height="538" alt="Screenshot 2026-04-22 105814" src="https://github.com/user-attachments/assets/8beaf781-7e50-476a-b552-59e55246830c" />

This [URL](https://kbcpenmarch.franceserv.com/23-mai-1925-5.html) reports the  `DISASTER OF MAY 23, 1925: ADDITIONAL INFORMATION
THE CEREMONY OF AUGUST 15, 1925`
(Article from the newspaper "La Dépêche de Brest" of August 16, 1925).
And in it, we come accross the list of crew members, and we found the youngest crew member too, as shown below.

<img width="1391" height="847" alt="image" src="https://github.com/user-attachments/assets/0949ba6a-43dd-4aba-a78b-a89233944ac3" />

Now, we need to just create the flag and submit it :
which will be `THM{Yves-Marie_Gourlaouen_15}, and there we get the flag.
Challenge completed !!!

<img width="567" height="95" alt="image" src="https://github.com/user-attachments/assets/f4bafbdc-fb1f-4dfe-8c5d-943088938c22" />










 
 




