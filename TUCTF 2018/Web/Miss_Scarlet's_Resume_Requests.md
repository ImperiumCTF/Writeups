## Miss Scarlet's Resume Requests - Web 398:  

**Description:** Something is up with Miss's Scarlet's acting site. Maybe you can take a look?  
**Challenge:** http://18.220.239.106/  
**Difficulty:** Easy  
**Solved by:** Tahar  

**Solution:**  
Open the URL, and head to: **http://18.220.239.106/contact.php**. And then we go to **http://18.220.239.106/Boddy/**.  
We open the source code of the web page and find something interesting hinting for the HTTP Method. We do a simple **CURL POST Request and get the Flag!!**  

```curl -X POST http://18.220.239.106/Boddy/```  

**Flag:**  
TUCTF{1_4ccu53_m155_5c4rl37_w17h_7h3_kn1f3_1n_7h3_h77p_r3qu357}
