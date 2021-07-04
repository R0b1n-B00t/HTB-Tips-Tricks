## Windows Tips


- [ ] The first version of Windows was a GUI for MS-DOS. Nowadays the most common Windows OSes and versions are listed below:


Operating System Names | Version Number
--- | --- 
Windows NT 4 | 4.0 
Windows 2000 | 5.0 
Windows XP | 5.1 
Windows Server 2003, 2003 R2 | 5.2 
Windows Vista, Server 2008 | 6.0 
Windows 7, Server 2008 R2 | 6.1
Windows 8, Server 2012 | 6.2
Windows 8.1, Server 2012 R2 | 6.3
Windows 10, Server 2016, Server 2019 | 10.0
  
  
- [ ] Using the `win32_OperatingSystem` class to get the Windows version number

```
> Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber

Version    BuildNumber
-------    -----------
10.0.19041 19041

```
Additional information on the `Get-WmiObject` command can be found here:

* [Example-oriented](https://adamtheautomator.com/get-wmiobject/)
* [Usage-oriented](https://ss64.com/ps/get-wmiobject.html)

  
