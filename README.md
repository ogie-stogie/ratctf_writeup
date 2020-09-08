# CSE 466: RAT CTF '20 Writeup
Taylor Bart<br>
September 5-6, 2020

## Overview
It was exciting to particpate in my first CTF event! I ended up choosing RAT CTF due to my experience in web development. Unfortunately, I was unable to retrieve any flags from this CTF but it was fun to learn about the different injection exploits such as XXE, XSS, and SSTI attacks. During the ctf, I spent the first half of my time trying to implement an XSS attack, then I moved on to looking for vulnerable network ports with nmap, and finally tried to implement XXE and SSTI attacks on the website.

## Information gathering
First I downloaded all the html’s that I could access so I could read and think about potential attack vectors.
I searched for any get methods so I could attack via the URL parameters, however none were found on the site.

## Looking for vulnerable ports
I used nmap to see what ports were open. 
I was able to find these open ports:
- 22/tcp
- 80/tcp
- 3000/tcp)

I tried using scp over ports 22, 80, 3000 to see if I could return the directory listing to my machine.

## XSS attacks
I began the CTF with XSS attacks since they were the most familiar to me. I began testing by trying to see if I could obtain an alert message when the HTML was interpreted. This would inform me of a XSS vulnerability that I could potentially exploit.
![](https://github.com/tbart27/ratctf_writeup/blob/master/Screenshot%20from%202020-09-07%2008-44-39.png)
I repeated this attack for every input on the login, register and upload pages, and I tried inserting it as a payload in the file that is uploaded to the site. The image above shows the payload being interpreted as text though. I tried various escape sequences and researched various XSS templates to attempt on these inputs for strings and files. However, I was never able to trick the Javascript and HTML into running my injected code and sending a simple alert to the browser interface.

## XXE attacks

## SSTI attacks

## CSRF attacks
Since the URL used some get methods, I tried various injections into the variables that were passed in the url. I was trying to see if there was an admin cookie that I could use to get access to the site. However, I quickly abandoned this attack since I wanted to gain access to the server and not necessarily mimic another user by using their cookies.

## jwt.io

