# Network Traffic Analysis

## Basics
* Run `zeek -Cr Basics.pcap`  
* Q1: Run `cat conn.log | zeek-cut id.orig_h id.resp_h proto | grep icmp` and compare with wireshark.
* Q2: Look for (no response) at the IMCP protocol in wireshark
* Q3: Look in wireshark for ARP and whois
* Q4: Look in the http.log file
* Q5: Run `cat http.log | grep .ico` to find which file was downloaded
* Then run `cat files.log | zeek-cut mime_type seen_bytes total_bytes | grep x-icon` to find the byte size.
* Q6: Look in the ftp.log file
* Q7: Look for "Please Specify Password" in the FTP section of wireshark, on the line above login successful.
* Q8: Look at the FTP-DATA for the LIST of /Ubuntu in wireshark, notice that one of the lines has a .gz which means it is not a directory.

## FTP
* Run `zeek -Cr FTP.pcapng`
* Q1: Look in the ftp.log file or in wireshark
* Q2: Follow the stream to copy the name: Pure-FTPd
* Q3, Q4, Q5: Found in the stream: CX3Data, f1leTransf3r, cookiejar
* Q6: Find the tcp part of the pcap where the file is being downloaded, follow that stream, change show data as to raw and save the file as flag.jpg. Then open the file and see the flag: SKY-BGHC-6641

## Printer
* Run `zeek -Cr Printer.pcap`
* Q1: Find the Print Job id by finding the print-job packet, open the IPP response and find job-id (integer): 16
* Q2: 
* Q3: Just look in wireshark
* Q4: myTest contains the data from the packet that started the print-job, `file myTest` returns `HP PCL printer data` `file --mime-type myTest` returns `myTest: application/octet-stream`
