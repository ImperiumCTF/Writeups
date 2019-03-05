## PWN - Secure Coding

**Challenge:** : [https://gitlab.tamuctf.com/root/pwn](https://gitlab.tamuctf.com/root/pwn)
**Difficulty:**: easy
**Solved by:** Neolex  

**Solution:**  
The goal of this challenge is to secure this vulnerable script: 
```C
#include <stdio.h>
#include <stdlib.h>

void echo()
{
	printf("%s", "Enter a word to be echoed:\n");
	char buf[128];
	gets(buf);
	printf("%s\n", buf);
}

int main()
{
	echo();
}
```
Here is the diff with the secured code : 
```diff
6c6
< 	printf("%s", "Enter a word to be echoed:\n");
---
> 	printf("Enter a word to be echoed:\n");
8,9c8,10
< 	gets(buf);
< 	printf("%s\n", buf);
---
> 	if(fgets(buf,128, stdin) != NULL){
> 		printf("%s\n", buf);	
> 	}
```

**Flag:**  
gigem{check_that_buffer_size_baby}

