# Pandora

Add the filter tcp && !(tcp.port==22) && !(tcp.port==80) to wireshark  
The server and client IP addresses can be seen in the first packet  
Open the packet to see the port  

Follow the tcp stream of the first packet
* The first four bytes represent the number of request 00 00 00 05 (5)
* The magic number is a 2 byte check (0417) use a hexadecimal to decimal converter and get (1047)
* The length of the request is the next 4 bytes (00 00 00 58), convert to decimal (88)
* The lenght of the second request is after the data, look for the next 00 00 00 pattern and find (00 00 00 48) -> (72)


### How many encryption requests were made by the client?
Count the TCP Options to get the answer (5)

### What is the length of the first encryption request?
