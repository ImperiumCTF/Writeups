## Crazy Train - Web 250:  

**Description:** N/A  
**Challenge:** fun.ritsec.club:3000  
**Difficulty:** Easy  
**Solved by:** Tahar Amine ELHOUARI  

**Solution:**  
We are presented with a web application that is based on **Ruby on Rails**, it is all about posting and submiting articles to the App!!  
When we try to submit an article, we are given two inputs to write in. The team took too much time, until I released that there is a hidden third input in the page. I have seen too many people (Probably Indians) trying to XSS the App, but I know that most of CTF contests doesn't have XSS in web challenges! It is a useless vulnerability in most of CTFs. So, I thought it is probably a command injection or probably an RCE. A friend from another team hinted me and told me that you are close, but there is a hidden input so I started trying with Command Injection but I did not succeed!  

Later, I started trying to exploit an RCE **Remote Code Execution**, It didn't work but the friend told me I am close! I remembered something, that this is a **Ruby on Rails** Challenge and not a PHP Web App Challenge, so I started thinking that exploitation payloade must be different because it is different language and different syntax! I started googling as usual and looking for guides about Web Application Hacking/Security in Web Apps that are based on Ruby on Rails, and I think that is the reason of the name of that challenge being named **Crazy Train**, because it is Crazy and Train refer to the Rails.  
After, googling I get to know how to exploita an RCE vulnerability and I succeeded using the following payload: **`cat flag.txt`**  

Note: I couldn't write the right payload of MD of github! Use **ALT GR + Number 7** in your keyboard to get the characters that I have used before & after **cat flag.txt**  
It is something like this ' cat flag.txt '  I hope you got my point!!

**Flag:**  
RITSEC{W0wzers_who_new_3x3cuting_c0de_to_debug_was_@_bad_idea}
