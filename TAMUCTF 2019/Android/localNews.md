## Local News - Android

**Description:** Be sure to check your local news broadcast for the latest updates!
**Challenge:** : app.apk
**Difficulty:** medium-hard
**Solved by:** Neolex  

**Solution:**  
The challenge give us an **apk**, this is the format of an **android application**.
I used **jadx** to analyze the decompiled code of the apk : 
```
$ jadx-gui --deobf ./app.apk
```
Let's look at the **MainActivity** code : 
```java
public class MainActivity extends AppCompatActivity {

    /* renamed from: com.tamu.ctf.hidden.MainActivity$1 */
    class C00141 extends BroadcastReceiver {
        C00141() {
        }

        public void onReceive(Context context, Intent intent) {
            Log.d(MainActivity.this.getString(C0017R.string.flag), Deobfuscator$app$Debug.getString(0));
        }
    }

    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView((int) C0017R.layout.activity_main);
        BroadcastReceiver hidden = new C00141();
        IntentFilter filter = new IntentFilter();
        filter.addAction(getString(C0017R.string.hidden_action));
        LocalBroadcastManager.getInstance(this).registerReceiver(hidden, filter);
    }
}
```
We can see a **BroadcastReceiver** being created, and the **onReceive** callback log the flag. I first thought I should trigger that callback but finally I decided to use **Frida** to run the function that returns the flag.
Here is my frida script : 
```javascript
'use strict;'

if (Java.available) {
    Java.perform(function() {
        var deobf = Java.use('io.michaelrocks.paranoid.Deobfuscator$app$Debug');
        var flag = deobf.getString(0);
        console.log('[+] flag: ' + flag);
    }
)}
```
In this  script I run the **getString** function of the **io.michaelrocks.paranoid.Deobfuscator\$app\$Debug** class with the arguments **0** like the BroadcastReceiver would do .
I run the frida-server and the challenge's application on my android emulator and run this command to run the script : 
```
$ frida -U com.tamu.ctf.hidden -l script.js
     ____
    / _  |   Frida 12.2.26 - A world-class dynamic instrumentation toolkit
   | (_| |
    > _  |   Commands:
   /_/ |_|       help      -> Displays the help system
   . . . .       object?   -> Display information about 'object'
   . . . .       exit/quit -> Exit
   . . . .
   . . . .   More info at http://www.frida.re/docs/home/
Attaching...                                                            
[+] flag: gigem{hidden_81aeb013bea}

```
**Flag:**  
gigem{hidden_81aeb013bea}


