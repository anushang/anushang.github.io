This challenge was simple and fun. As it involved overflowing beer ;)
![_config.yml]({{ site.baseurl }}/images/bofgit2.png)

as you can guess by the looks of it, it's a buffer overflow challenge and all we have to do is overflow the stack and get our stack pointer to point to a location in a memory which we can take advantage of.
Let's quckly check if is vulnerable to the attack.
![_config.yml]({{ site.baseurl }}/images/bofgit1.png)

bingo!
We just sent random characters and we go a segmentation fault error!
So all now we have to do are these things:
1. Reverse the ELF and find something to jump upon.
2. Find it's address on stack.
3. Make a python script to pwn the challenge.
There are many ways to do this. We can use Ghidra to find what ELF do and what their funcions do. I will just list the functions using
```
objdump -d beer
```
In the output the function flag looks interesting.
![_config.yml]({{ site.baseurl }}/images/gitbof3.png)

Jot down the address of the function and now we have to make simple python script to launch the attack.


