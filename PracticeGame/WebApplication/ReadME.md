# Web Application Exploitation

## Amoonguuss
`https://3c820b188b25e2d0fca91da95f8f3672-amoonguss.web.cityinthe.cloud/`  
### Instructions
There's a new game in the city called Amoonguss and seems like you could hack it pretty easily, demonstrate the vulnerability by successfully winning 30 rounds of the game. The game maker has also put a few flags in there to reward you as you try to pentest the web app.  

### Flag 1
* Open the dev tools, go to debugger and open the index file. 
* Flag 1 is found on line 21
* `Flag 1: SKY-CODE-4012`

### Flag 2
* Set a breakpoint on line 28 (the line that refreshes the window)
* In the networks tab, look at the request from sending a vote
* Flag 2 is found in the response headers
* `Flag 2: SKY-YHMB-5390`

### Flag 3
Ideas to move on: intercept the response with burp?

## Rec Center Login
`https://3af64cde8d51a516fadd5a6f59fb71b4-login.web.cityinthe.cloud/`  
Complete a security audit

### What database software is being used by the login system?

