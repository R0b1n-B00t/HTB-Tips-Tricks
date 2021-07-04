## Basic rules for Scanning & Enumeration


- [x] In this guide *Linux* commands are anticipated by **#** while *Windows* ones are preceded by **>**. If no one character is present, it means that the command works in both OSes.
- [x] **10.10.10.101** -> *Target machine* 
- [x] **10.10.10.5** -> *Attacker machine*

##

- [ ] *TCP scan* - Always perform a Nmap scan of the target (the following options may be useful: **-sC** to run Nmap scripts, **-sV** to perform a version scan and **-p-** to scan all the 65535 ports)
  
  `# nmap -sC -sV -p- 10.10.10.101`

##

- [ ] *Additional scripts* - Once identified the main services,search for additional Nmap scripts to run (both locally or externally with a Web Search Engine)

```
# locate scripts/cups        
/usr/share/nmap/scripts/cups-info.nse
/usr/share/nmap/scripts/cups-queue-info.nse

```

##

- [ ] *Search for Public Exploit* - It sounds strange but searching for Public Exploits at this stage is a good practice to adopt and somethimes it gives you joys 
  
  `# searchsploit drupal 7` and to download something that could be interesting: `# searchsploit -m php/webapps/35150.php`
  
  `# msf6 > search drupal 7` be sure to repeat the search even from the Metasploit Framework
  
  Complete the research by the means of Google, DuckDuckGo, etc.
  
##  
  
- [ ] *Banner grabbing* - Perform banner grabbing requests on the target open ports identified and collect them
  
  `# nc 10.10.10.101 21` 
  
  or through the Nmap banner script, which can be used even to query a whole subnet
  
  `# nmap -sV --script=banner -p21 10.10.10.0/24` 
  
##
  
- [ ] *Check SMB* - Always check SMB if it is available
  
  `# nmap --script smb-os-discovery.nse -p445 10.10.10.101` and `# nmap -A -p445 10.10.10.101`
  
  Try to enumerate shared folders by the means of *smbclient* with the following options (**-N** to suppress password prompt and **-L** to retrieve the list of shares)
  
  `# smbclient -N -L \\\\10.10.10.101`
  
  Attempt to connect as a guest user, as follow
  
  `# smbclient \\\\10.10.10.101\\users`
  
  Try any username and password found during enumeration in order to login via SMB (here the username *yoda* is used to login)
  
  `# smbclient -U yoda \\\\10.10.10.101\\users`
  
##

  - [ ] *Investigate SNMP* - Do not forget to enumerate SNMP communities if this service is used by the target
  
  `# snmpwalk -v 2c -c public 10.10.10.101 1.3.6.1.2.1.1.5.0` in order to look for Public Communities
  
  `# snmpwalk -v 2c -c private 10.10.10.101` in order to search for Private Communities as well
  
  Somethimes it could be useful to brute force SNMP community string names by the means of a dictonary, as follow
  
  `# onesixtyone -c onesixtyone/dict.txt 10.10.10.101` the file *dict.txt* is part of the onesixtyone official repository ( [onesixtyone](https://github.com/trailofbits/onesixtyone) ) and typically it works very well!
  
