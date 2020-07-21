### SMB :
      smbclient -U "" -L //<ip>         ->  -L flag Get a list of shares available on a host
      smbcleint -U "" //<ip>            ->  Connects to our users shares
 
       smb: \> recurse on               ->  Recursively list the contents
       smb: \> ls
       
       mget                             ->  Downloads file
       
       smbget -R smb://<ip>/path/ -U "" -> -R flag recursive download smbfiles owned by -U
       
