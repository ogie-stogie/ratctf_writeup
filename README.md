# CSE 466: RAT CTF '20 Writeup
Taylor Bart<br>
September 5-6, 2020

## Overview
It was exciting to particpate in my first CTF event! I ended up choosing RAT CTF due to my experience in web development and since it was mentioned that this would be an easier CTF. Unfortunately, I was unable to retrieve any flags from this CTF but it was fun to learn about the different injection exploits such as XXE, XSS, and SSTI attacks. During the ctf, I spent the first half of my time trying to implement an XSS attack, then I moved on to looking for vulnerable network ports with nmap, and finally tried to implement XXE and SSTI attacks on the website.

## Information gathering
After reading the information for this event, I knew I would have to focus on XSS and XXE attacks. I then downloaded all the html’s that I could access so I could read and think about potential attack vectors. I noted every input across the site and wrote them down for later injection testing. Further, I used nmap to see what connections were open and my focus was on creating an ssh to the server so that I could map out the inner file system and search for methods to escalate my command's privildges.

## Looking for vulnerable ports
I proceeded to read over documentation of telnet, netstat, scp and nmap to see what methods I could potentially use to escape my Docker container or possibly exploit another network vulnerability.

The most promising data I found was when I used nmap to see what ports were open. I was able to find these open ports:
- 22/tcp
- 80/tcp
- 3000/tcp)

I tried using scp over ports 22, 80, 3000 to see if I could return the directory listing to my machine. I believe I needed to be able to open up ssh over the port first but no vulnerability was found by me that would give me the priviledges to accomplish that.

## XSS attacks
I began the CTF with XSS attacks since they were the most familiar to me. I began testing by trying to see if I could obtain an alert message when the HTML was interpreted. This would inform me of a XSS vulnerability that I could potentially exploit. Here is a screenshot of one of the injection attempts I made on the site:

![](https://github.com/tbart27/ratctf_writeup/blob/master/Screenshot%20from%202020-09-07%2008-44-39.png)
<br>
I repeated this attack for every input on the login, register and upload pages, and I tried inserting it as a payload in the file that is uploaded to the site. The image above shows the payload being interpreted as text though. I tried various escape sequences and researched various XSS templates to attempt on these inputs for strings and files. However, I was never able to trick the Javascript and HTML into running my injected code and sending a simple alert to the browser interface.

## XXE attacks
I attempted some template XXE attacks in a similar manner to the XSS attacks. However since I couldn't find any XML files nor did I know the structure of any possible XMLs on the server, this turned out to be a rabbithole that wasted hours I could've spent towards other methods. I tried to keep coming back to this method since it was mentioned many times in the introductory materials to this event.

## CSRF attacks
Since the URL used some get methods, I tried various injections into the variables that were passed in the url. I was trying to see if there was an admin cookie that I could use to get access to the site. However, I quickly abandoned this attack since I wanted to gain access to the server and not necessarily mimic another user by using their cookies.

## SSTI attacks and jwt.io
After the CTF, XSS Rat left some hints about using SSTI (server-side template injection) to retrieve information about the site! Since I was more familiar with building websites with browser-side interactions in mind, I never thought to look for server side injections. I spent my last hour researching SSTI theory and testing some examples to see what I could return. In the end, it seemed like I repeated the original XSS attacks but with linux server commands, but I was unable to escape the strings and make the code executable. Currently, I am still going over the site and looking into hints about jwt.io tokens.

## Summary
