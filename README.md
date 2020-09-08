# CSE 466: RAT CTF '20 Writeup
Taylor Bart<br>
September 5-6, 2020

## Overview
Unfortunately, I was unable to retrieve any flags from this CTF but it was fun to learn about the different injection exploits such as XXE, XSS, and SSTI attacks. During the ctf, I spent the first half of my time trying to implement an XSS attack, then I moved on to looking for vulnerable network ports with nmap, and finally tried to implement XXE and SSTI attacks on the website.

## Information gathering
First I downloaded all the html’s that I could access so I could read and think about potential attack vectors.
I searched for any get methods so I could attack via the URL parameters, however none were found on the site.
I used nmap to see what ports were open (22/tcp, 80/tcp, 3000/tcp)

![img1]()
