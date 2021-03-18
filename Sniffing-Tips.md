## Sniffing Tips


- [x] In this guide *Linux* commands are anticipated by **#** while *Windows* ones are preceded by **>**. If no one character is present, it means that the command works in both OSes.


- [ ] If you are looking for an easy way to capture common plaintext passwords via **tcpdump**, you can try to use the following command:
  
  `# tcpdump port http or port ftp or port smtp or port imap or port pop3 or port telnet -l -A | egrep -i -B5 'pass=|pwd=|log=|login=|user=|username=|pw=|passw=|passwd=|password=|pass:|user:|username:|password:|login:|pass |user '`
