<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/1badcc97-e0da-47be-9d29-6bfd5f0a1bfb" />

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


 
 




