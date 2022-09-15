# NCL Fall 2022 Log Analysis

## Contents


## Nginx
### IP
use `awk '{print $1}' access.log > IP.txt` to save the *IP* addresses in their own file.  
use `cat IP.txt | sort -n | uniq | wc -l` to get the number of unique IP addresses.  

### 200 and 400 Status
use `cat access.log | grep " 200 " > statusCode.txt` to save the lines containing the status codes to its own file.  
use `cat statusCode.txt | wc -l` to count the lines. Each line is its own request.  
use `cat access.log | grep " 400 " > statusCode400.txt` to save the lines containing the *400* status code to its own file.  
use `cat statusCode400.txt | wc -l` to count the lines. Each line is its own request.  

### Doorbell
This one is a little tricky...  
use `grep doorbell access.log`  
This didn't work. Looking through the *access.log* file I realized that doorbell was spelled "dorbell", with only one "o".  
use `grep dorbell access.log` to get the answer.  

### Googlebot Version
use `grep Googlebot access.log` to find the version.  

### Shellshock
Did some research on the *Shellshock Vulnerability*, and found that it uses *bash* to gain control over a system.  
use `grep bash access.log` to return all lines with "bash" in them.  
One *IP* shows up in two requests.  

### Most Popular Firefox Version
use `grep Firefox access.log > firefoxVersion.txt` to get all requests containing "Firefox" to their own file.  
There are not very many so just counting yourself is fine.  

### Most Common HTTP Method
use `cat access.log | wc -l` to count all requests.  
use `cat access.log | grep GET | wc -l` to count the requests using the "GET" method.  
Since "GET" had 60 hits it has to be the most common one since there are 99 total requests.  

### Second most common HTTP Method
use `cat access.log | grep CONNECT | wc -l` 
use `cat access.log | grep POST | wc -l`

### How Many Requests Were For \x04\x01\x00P\xC6\xCE\x0Eu0\x00
To grep backslashed, an additional backslash is needed in front of each backslash and single quotes need to be used.  
use `grep '\\x04\\x01\\x00P\\xC6\\xCE\\x0Eu0\\x00' access.log | wc -l` to get the number of requests.  

## History (medium)

### What did the user search for on craigslist
Open in SQL Browser on Kali.  
Go to *Browse Data* and choose the *moz_places* table.  
Click on the entries containing craigslist, one of them will have the word search in them.  
`http://baltimore.craigslist.org/search/sss?sort=rel&query=bitcoin`, the queary tells us what they searched for.  

### What was the current price of bitcoin when the user was browsing
Look in the title field.  
One of the entries will have a *$* in it.  
`($239.5) Bitstamp - buy and sell bitcoins`

### What bitcoin exchange did the user log in to
In the *url* field, look for login or signin.  
`https://www.coinbase.com/signin`  
`https://www.coinbase.com/signin_step_two`  
`https://www.coinbase.com/accounts/primary`  
These three entries indicates that the user logged in to coinbase. 

### What is the email that was used to log into the exchange
The only email found in the *title* field is `b1gbird@gmail.com`.  

### What was the ID of the Bitcoin transaction that the user looked at
Scroll down and see *blockchain* in the urls. One of them has the word *transaction* in the *title* field. Copy the hash from the url.  

### What was the total BTC value of all the inputs of the Bitcoin transaction
Search for the transaction ID in a browser.  
`https://www.blockchain.com/btc/tx/5274cfba585a4b5681527a37f95c76340428916bb7480cef6c545f0a28dcd2d7?show_adv=false`  
Scroll down and find the *Total Input* field.  

### Which bitcoin address received the majority of the Bitcoin in the transaction?
On the same website, scroll down to outputs and compare the outputs to the different addresses.  

## Squid (hard)

### In what year was this log saved?


### How many milliseconds did the fastest request take?
use `grep -Eo " [0-9]{1,3} " squid_access.log > milliseconds.txt`, to put the milliseconds in their own file.
use `grep -Eo " [0-9]{1,8} [0-9]" squid_access.log > milliseconds.txt` instead, to only grab data from the milliseconds field, ignore the *1* next to the number.
use `cat milliseconds.txt | sort -nr `, to display the shortest time at the bottom.


### How many milliseconds did the longest request take
use `grep -Eo " [0-9]{1,8} [0-9]" squid_access.log > milliseconds.txt` instead, to only grab data from the milliseconds field, ignore the *1* next to the number.  
use `cat milliseconds.txt | sort -n `, to display the longest time at the bottom.  

### How many different IP addresses did the proxy serve?
use `grep -Eo "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3} T" squid_access.log > IP.txt ` to put them in a seperate file.  
use ` cat IP.txt | sort -n | uniq | wc -l` to get the number of unique IP addresses.  

### How many GET requests were made?
use `grep GET squid_access.log | wc -l` to display the number of *GET* requests.  

### How many POST requests were made?
use `grep POST squid_access.log | wc -l` to display the number of *POST* requests.

### What company created the antivirus used on the host at 192.168.0.224?
use `grep virus squid_access.log`, to display the lines containing virus.  
Make sure the IP address match, investigate the url for something that could be a company name, google it.

### What url is used to download an antivirus update?
It is the link displayed from the previous command.  