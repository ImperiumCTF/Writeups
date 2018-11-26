## Colonel Mustard's Simple Signin - Web 172:  

**Description:** We know Col Mustard is up to something--can you find a way in to tell us what?  
**Challenge:** http://13.59.239.132/  
**Difficulty:** Easy  
**Solved by:** Tahar  

**Solution:**  
We open up the challenge URL as usual, we notice the same login form! But of course it shouldn't be the same solution or same challenge =)  
From previous experience as usual from too many CTFs, most of those logins forms are meant to say **SQLi Form Login Bypass** and it means bypassing the login form by injecting a **Structure Query Language** Payload. We use the following payload and boom flag:  
```' or ''='```
```' or ''='```

**Flag:**  
TUCTF{1_4ccu53_c0l0n3l_mu574rd_w17h_7h3_r0p3_1n_7h3_l061n}
