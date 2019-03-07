## Science - Secure Coding

**Challenge:** : [https://gitlab.tamuctf.com/root/science](https://gitlab.tamuctf.com/root/science)
**Difficulty:**: easy
**Solved by:** Neolex  

**Solution:**  
The goal of this challenge is to secure the vulnerable Flask script of the web challenge Science! . 
Here is the vulnerable script :  
```python
import requests
import json
import sys
from tamuctf import app
from flask import Flask, render_template, request, jsonify, render_template_string

@app.route('/')
@app.route('/index')
def index():
    
    return render_template('index.html')

@app.route('/science', methods=['POST'])
def science():
    try:
        chem1 = request.form['chem1']
        chem2 = request.form['chem2']
        template = '''<html>
        <div style="text-align:center">
        <h3>The result of combining {} and {} is:</h3></br>
        <iframe src="https://giphy.com/embed/AQ2tIhLp4cBa" width="468" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div>
        </html>'''.format(chem1, chem2)

        return render_template_string(template, dir=dir, help=help, locals=locals)
    except:
        return "Something went wrong"

```
Here is the diff with the secured code : 
```diff
20c20
<         <h3>The result of combining {} and {} is:</h3></br>
---
>         <h3>The result of combining {{chem1}} and {{chem2}} is:</h3></br>
22,24c22,23
<         </html>'''.format(chem1, chem2)
< 
<         return render_template_string(template, dir=dir, help=help, locals=locals)
---
>         </html>'''
>         return render_template_string(template,chem1=chem1,chem2=chem2,dir=dir, help=help, locals=locals)
27d25
< 
```

**Flag:**  
gigem{br0k3n_fl4sk_2d88bb862569}

