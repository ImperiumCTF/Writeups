## Yeahright - Reverse 149:  

**Description:** What an insensitive little program. Show it who's boss!  
**Challenge:** yeahright + flag + nc 18.224.3.130 12345  
**Difficulty:** Easy  
**Solved by:** Tahar  

**Solution:**  
We download both files, the **flag** file isn't really an important file for the Challenge but it is good to test out if you are right or not!  

I started by reverse engineering the **yeahright** binary file after using the **file** command to get some usefull information before reversing it!!  

By reversing the file we find the needed password so when we connect to the online challenge service we use it and get the real **flag**.  

I tried the founded password and it just worked! Another simple trick is to use a **HEX Editor** It is easy and fast to get the password!! or you can use **IDA Pro** a GUI based Reverse Engineering framework that will get the job done in an easy and fast way!! Instead of using Radare2 or GDB or that kind of CLI based toolkits.  

**Flag:**  
TUCTF{n07_my_fl46_n07_my_pr0bl3m}
