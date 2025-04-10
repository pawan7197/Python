# Python
Flask app deployement

 
1. Launch EC2 and Connect via SSH

- Go to AWS EC2 dashboard.
- Launch an instance (Ubuntu 24.04).
- Choose a key pair or create a new one.


Now, connect to the EC2 instance from your local terminal:
```bash
cd Downloads
ssh -i "python.pem" ubuntu@ec2-18-234-210-68.compute-1.amazonaws.com
```

2. Update and Install Dependencies
Run the following commands 
```bash
sudo apt update
sudo apt install -y libmariadb-dev gcc g++ build-essential python3-dev dh-python python3-venv
```
3. Create Flask App
Make a new directory and create the app
```bash
mkdir app1
cd app1
vim main.py
```
Now Paste this content in `main.py` and save.
```bash
from flask import Flask, jsonify
import random

app = Flask(__name__)

quotes = [
    "Push yourself, because no one else is going to do it for you.",
    "Success is not final; failure is not fatal.",
    "Dream it. Wish it. Do it."
]

@app.route("/quote")
def get_quote():
    return jsonify({"quote": random.choice(quotes)})

if __name__ == "__main__":
    app.run(port=5001, debug=True)
```

4. Setup Virtual Environment and Install Flask
```bash
python3 -m venv myenv
source myenv/bin/activate
pip install flask
```

5. Now Create WSGI File
Create a file named `wsgi.py`:
```bash
vim wsgi.py
```
Now Paste this code.

from main import app as application
```bash
if __name__ == "__main__":
    application.run(host='0.0.0.0', port=5001)
```

6. Now Install Gunicorn and Run the App
```bash
pip install gunicorn
gunicorn --bind 0.0.0.0:5001 wsgi
```
- Open the inbound rules in EC2 security group and add, edit the rule then save it,
 ```bash
     SSH - TCP - Port 22 - Source: 0.0.0.0/0
     Custom TCP - Port 5001 - Source: 0.0.0.0/0
```
Now  Flask app is live,
```bash
http://18.234.210.68:5001/quote
```
now we can see a random motivational quote in JSON format.
```bash
{
  "quote": "Push yourself, because no one else is going to do it for you."
}
```
🎉 Deployment Successful!
```bash
![Image](https://github.com/user-attachments/assets/f6530037-8ebd-42cc-8823-73214eefb04f)
```
