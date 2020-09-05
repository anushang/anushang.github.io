How to restrict someone debugging your program just add this:
```c
if (ptrace(PTRACE_TRACEME, 0, 1, 0) < 0)
    {
      printf("[-] Don't use a debugguer !\n");
      abort();
      }
```
