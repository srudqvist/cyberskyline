# TelNet (Easy)  

## Workflow
Open the pcap in wireshark and click follow tcp stream  
* Get the username by realizing that tteeeeesssttt was not the username, try test instead
* The password was correct in the tcp stream
* Get the command issued from the same tcp stream and use the knowledge gained from the username to realize it is `uname -a`
* The year is displayed from the uname -a command
* Get the hostname by copying it from the tcp stream `cm4116 2.6.30.2-uc0`
* The cpu architecture is also displayed in the stream

## Answers  
1. "test"
2. "capture"
3. "uname -a"
4. "2011"
5. "cm4116 2.6.30.2-uc0"
6. "armv4tl"