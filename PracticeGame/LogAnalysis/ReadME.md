# Log Analysis

## Virus Scan
Just read through the log

## Error Log
1. `cat error.log | grep "File does not exist:" | wc -l`

### Unique IP Adresses
use `awk '{print $8}' error.log > IP.txt` to save the IP Adresses to their own file
then use `cat IP.txt | sort -n | uniq | wc -l`  

### What IP Adress generated the most errors
use `cat IP.txt | sort -n | uniq -c | sort -nr > counted.txt` then look in the file, the top one is the most occurring one

### What IP Adress scanned for the most unique files
use `awk '{print $8 $13}' error.log > IP_and_file.txt` to get a file containing the IP adresses and the files.  
use `cat IP_and_file.txt | sort -n | uniq | > unique.txt` to get a file with all the unique ones.  
use `awk -F"]" '{print $1}' unique.txt | uniq -c | sort -nr > counted2.txt` to get the one with the most unique files on the top.  

### Using the device with the IP address from the previous question, how many unique files/directories (case-sensitive) did the device request that yielded a "File does not exist error"?
used `cat error.log | grep "176.53.21.162] File does not exist: " | wc -l`
2018 
or `cat error.log | grep "176.53.21.162] File does not exist: " | sort -n | uniq | wc -l`     
1680  
and `cat error.log | grep "176.53.21.162] File does not exist: " | sort -n | uniq > q5.txt`  
DId not get correct ans

## IDS

### How many unique dest IP?
use `sed -e 's/\([0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+\).*$/\1/' -e t -e d eve_alert.json | sort | uniq > IP.txt`  
then `cat IP.txt | grep 'dest' > destOnly.txt`   
then `cat destOnly.txt | sort -n | uniq | wc -l`  

### How many unique signatures were recorded?
use `cat eve_alert.json | grep "signature_id" > signature_id.txt`  
then `cat signature_id.txt | sort -n | uniq | wc -l`  

### What is the most common attack category?
use `cat eve_alert.json | grep '"category":' > category.txt`  
then `cat category.txt | sort -n | uniq -c | sort -nr > countedCategory.txt`  
then open the countedCategory file to see the most common one on the top.  

### What is the most common attack signature?
use the same commands as the one before but look for signature.  

### How many total bytes are sent to the IP 10.47.8.20?


### How many seconds elapsed during this log?

"2021-10-01T07:00:00.000Z",
"2021-10-12T16:50:14.000Z"


985,814  
D: 11  
H: 9  
M: 50  
S: 14  

### What is the category involved in alerts that are not TCP based traffic?
use `cat eve_alert.json | grep '"proto": "' > proto.txt `  
then `cat proto.txt | sort -n | uniq -c | sort -nr > countProto.txt`  
open countProto.txt and see UDP.  
use ctrl-f and search for UDP in the json file.  
copy the category value.  

