## Professor Plum's Ravenous Researcher - Web 474:  

**Description:** Professor Plum is hiring! Maybe you can get the job!  
**Challenge:** http://18.223.185.148/  
**Difficulty:** Medium  
**Solved by:** Tahar  

**Solution:**  
That was the hardest challenge between all WEB Challenges!! Took too many hours to get it done :-3  
We open the URL as we used to do with **Web Challs**. Following the redirections we get into this page: **http://18.223.185.148/search.php**. I've received a hint from an Organizer, saying that I must link the other web challs names to solve this one and do more OSINT!!. And now, ideas started getting into my mind =)  

Googled too many times about the names of the other web challenges, and I found out that it is a **Clue Board Game**. And that's the official WikiPedia page that helped me a lot to get this challenge done:  
```https://en.wikipedia.org/wiki/Cluedo```  

Since, the challenge is talking about the locations, so I went directly to the **Rooms** section! ```billiard room``` was the right location!! It worked and now the page is saying something else!! Now, I started overthinking!  

I thinked about running BurpSuite so I can play with that WebApplication the right way ;-)  

I started getting angry and frustrated and damn tired and sleepy (It was 4AM), I just noticed that there is a parameter being sent to the server with the **Cookies Value: 0**. What I did is that I just changed that cookie parameter from 0 to **1** and boom it worked!! Finally x'D  

**Flag:**  
TUCTF{1_4ccu53_pr0f3550r_plum_w17h_7h3_c00k13_1n_7h3_b1ll14rd_r00m}
