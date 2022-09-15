# NCL Fall 2022 Log Analysis

## One

Run `aircrack-ng PCAP1.pcap` to find the answers to questions 1,2,4.  

### What is the key size of the wireless network data encryption method in bits?
The key is `A4:81:53:B4:CF`, 5 bytes, each byte has 8 bits, 5*8=40.   
Search the web for WEP Keys and find one that matches the key size of 40 bits, giving us a 64 bit encryption method.  

### What is the TCP checksum of the first packet in the capture (in hex)? 
In Wireshark, go to edit, preferences, protocols and select IEEE 802.11, and select "enable decryption".  
Then click "edit" decryption keys and add the key from aircrack.  
Hit "okay", now the checksum should be visible.  

### What is the IV for the first packet in the capture in hexadecimal representation?
Find the Initialization Vector value by clicking it in the pcap.

