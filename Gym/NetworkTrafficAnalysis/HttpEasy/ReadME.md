# HTTP (Easy) 

## How I found the answers

Download the *HTTP2.pcap* file.  
run `source /etc/profile.d/zeek.sh` to reload the file path for zeek.  
run `zeek -C -r HTTP2.pcap`.  
run `head http.log` to see the *linux tool* and *IP* addresses.  

## What is the name of the web server software that handled the request?
Right click the GET request in Wireshark, click follow tcp stream and see nginx in the new window.  

## What is the md5sum of the file downloaded?
Save the file by clicking File, Extract Object and choose the file.  
then use `cat logo.png | md5sum` to get the md5sum


## answers
1. Wget
2. "nginx"
3. 192.168.1.140
4. 174.143.213.184
5. 966007c476e0c200fba8b28b250a6379
