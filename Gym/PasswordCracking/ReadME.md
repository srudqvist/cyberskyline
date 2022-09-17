# Password Cracking


## Cracking 2 (medium)
These passwords have a pattern so we can use *hashcat* with the mask "SKY-HQNT-?d?d?d?d"  
Using *hash identifier* we find the format of the hashes, the first one is: `md5(strtoupper(md5($pass)))`

### Hashcat
* Use `-m` for the type, "0" is md5, "4300" is md5(strtoupper(md5($pass)))
* Use `-a` for the attack mode, "3" is brute force
* Command for the first one: `hashcat -m 4300 -a 3 71b816fe0b7b763d889ecc227eab400a "SKY-HQNT-?d?d?d?d"
`  
* Gave two options `Candidates.#1....: SKY-HQNT-0416 -> SKY-HQNT-6497` 

* Command for first one `hashcat -m 0 -a 3 71b816fe0b7b763d889ecc227eab400a "SKY-HQNT-?d?d?d?d"
`  
* Gave two different options `Candidates.#1....: SKY-HQNT-3786 -> SKY-HQNT-2984`

## Windows Passwords
* Download the XP Special Rainbow Tables from sourceforge.net  
* Then open **ophcrack** in Kali.  
* Press *load single hash*, add the hash
* Press *Tables* Locate the XP Special Rainbow Table
* Press *Crack*