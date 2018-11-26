## hardDOS - Misc 497:  

**Description:** Paying attention is mitey important! (Difficulty: Hard)  
**Challenge:** nc 18.216.100.42 12345  
**Difficulty:** Medium  
**Solved by:** Tahar & Yanis  

**Solution:**  
We start by connecting to the given target, we follow the instructions that are printed out on the remote server and then choose the option **2**. Then we choose **y**. We start by injecting the following payload to get all files listed in the challenge's server: ```$(ls)```.  

We check all the files by running ```file FILENAME``` so we can check the type of every file following the challenge instructions!! We find an interesting file **GRAPHICS.COM**.  

We run the **strings** command to see what is in there since we can't use the **type** command:  
```strings GRAPHICS.COM```  

**Flag:**  
TUCTF{4LW4Y5_1NF3C7_7H353_19742_BY735}
