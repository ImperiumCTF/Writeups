## Easter Egg: Crystal Gate - Web 446:  

**Description:** I don't wanna go anywhere.  
**Challenge:**http://18.191.227.167/  
**Difficulty:** Easy  
**Solved by:** Tahar  

**Solution:**  
Open the URL, after simple and quick directory bruteforcing we find a directory **.git**. We download the Index file: **http://18.191.227.167/.git/index**. We open that downloaded file using a Hex Editor and theb we find an interesting folder/file!!  


**http://18.191.227.167/crystalsfordays/traversethebridge.php** The hint is saying **Note2: I can't seem to remember the param. It's "file"**  We use that file parameter and exploit it. It is an **LFI Vulnerability (Local File Inclusion)**.  

**http://18.191.227.167/crystalsfordays/traversethebridge.php?file=** We use this URL to exploit the vulnerability, and it becomes:   
```http://18.191.227.167/crystalsfordays/traversethebridge.php?file=../../```. We find too many files and the interesting one was **TheEgg.html**.  

When we open that file:
**http://18.191.227.167/crystalsfordays/traversethebridge.php?file=../../TheEgg.html** we get the flag!  

**Flag:**  
TUCTF{3_15_4_M4G1C_NUMB3R_7H3_crys74L_k3Y_15_y0ur5!}
