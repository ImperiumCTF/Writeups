## Space Force - Web 100:

**Description:** The Space Force has created a portal for the public to learn about and be in awe of our most elite Space Force Fighters.  
**Challenge:** fun.ritsec.club:8005  
**Difficulty:** Easy  
**Solved by:** Milan  

**Solution:**  
We are provided with an URL: http://fun.ritsec.club:8005/  
When we open the challenge, we can see that we are presented with Ship leaderboard If we enter one of the presented ships, we can see its records. If we type **'**, the text changed to **Something went wrong with your record query! What are you trying to do???** Which clearly indicates that this is an SQL injection Vulnerability!

We can just query all records by using the following payload: **' or 'x'='x**  

**Flag:**
RITSEC{hey_there_h4v3_s0me_point$_3ny2Lx}
