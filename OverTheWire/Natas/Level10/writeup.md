# Natas Level 10
## Credentials 
username : natas10

URL : http://natas10.natas.labs.overthewire.org/
## Aim
to get the password of the next level.
## Solve 
On entering the url , we are asked to enter the username and password, as shown below :

<img width="860" height="353" alt="image" src="https://github.com/user-attachments/assets/fefc4314-73e1-4a71-a796-856231ab6478" />

On correct credentials input we get a web page something like this : 

<img width="1217" height="343" alt="image" src="https://github.com/user-attachments/assets/f7fe3a5a-dde6-4a1f-b7ac-9407a03276dc" />

Now, we must read the source code to analyze : 

<img width="906" height="682" alt="image" src="https://github.com/user-attachments/assets/236c4efb-860d-4d3e-a525-42a12fbca669" />

The logic as a filter, which is their to protect for the injection attempt, lets analyze it : 
```

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
```
We understand that , `; | & ` will be blocked and we cannot use them for injection, but except for that we can use anything.
We are going to use the `Regex`.
```
⭐⭐ Regex Cheat Sheet ⭐⭐

⭐ Core Regex Patterns

| Symbol | Meaning              | Example               | Explanation                 |
|--------|----------------------|-----------------------|-----------------------------|
| `.`    | Any single character | `grep . file.txt`     | Matches all non-empty lines |
| `*`    | Repeat (0 or more)   | `a*`                  | Matches "", "a", "aa", etc. |
| `.*`   | Match everything     | `grep .* file.txt`    | Matches almost all lines    |
| `^`    | Start of line        | `grep ^a file.txt`    | Lines starting with `a`     |
| `$`    | End of line          | `grep a$ file.txt`    | Lines ending with `a`       |
| `^$`   | Empty line           | `grep ^$ file.txt`    | Matches only empty lines    |
| `[abc]`| Any one character    | `grep [abc] file.txt` | Matches `a`, `b`, or `c`    |
|`[^abc]`| Not these characters | `grep [^a] file.txt`  | Matches anything except `a` |
| `\`    | Escape character     | `grep \. file.txt`    | Matches literal `.`         |

---

⭐ CTF / Pentesting Usage

| Goal                | Pattern  | Example              | Result                    |
|---------------------|----------|----------------------|---------------------------|
| Print all lines     | `.`      | `grep . file.txt`    | Shows all non-empty lines |
| Print everything    | `.*`     | `grep .* file.txt`   | Shows all lines           |
| Unknown content     | `.`      | `grep . secret.txt`  | Dumps content             |
| Match specific word | `word`   | `grep pass file.txt` | Shows lines with "pass"   |
| Start match         | `^word`  | `grep ^root file.txt`| Lines starting with root  |
| End match           | `word$`  | `grep sh$ file.txt`  | Lines ending with sh      |

---

⭐ Key Concepts

| Concept         | Explanation                   |
|-----------------|-------------------------------|
| Grep Behavior   | Prints only matching lines    |
| No Output       | Pattern didn't match anything |
| Full Output     | Pattern matches everything    |
| Best Dump Trick | Use `.` or `.*`               |

---

⭐ Golden Rule

> If your pattern doesn't match → no output  
> If your pattern matches everything → full output  

---

⭐ Quick Memory

| Pattern | Meaning    |
|---------|------------|
| `.`     | wildcard   |
| `*`     | repeat     |
| `.*`    | everything |
```
