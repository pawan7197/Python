# Python
Flask app deployement

This guide walks you through the step-by-step deployment of a simple Python Flask web application on an AWS EC2 instance. The app is served using Gunicorn with a WSGI interface.

1. Launch EC2 and Connect via SSH

- Go to AWS EC2 dashboard.
- Launch an instance (Ubuntu 24.04).
- Choose a key pair or create a new one.
- Open the following inbound rules in your security group:
    • SSH - TCP - Port 22 - Source: 0.0.0.0/0
    • Custom TCP - Port 5001 - Source: 0.0.0.0/0

Now, connect to the EC2 instance from your local terminal:


cd Downloads
ssh -i "python.pem" ubuntu@ec2-18-234-210-68.compute-1.amazonaws.com


2. Update and Install Dependencies
Run the following commands 

sudo apt update
sudo apt install -y libmariadb-dev gcc g++ build-essential python3-dev dh-python python3-venv

3. Create Flask App
Make a new directory and create the app

mkdir app1
cd app1
vim main.py

Now Paste this content in `main.py` and save.

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

4. Setup Virtual Environment and Install Flask

python3 -m venv myenv
source myenv/bin/activate
pip install flask

5. Now Create WSGI File
Create a file named `wsgi.py`:

vim wsgi.py

Now Paste this code.

from main import app as application

if __name__ == "__main__":
    application.run(host='0.0.0.0', port=5001)

6. Now Install Gunicorn and Run the App

pip install gunicorn
gunicorn --bind 0.0.0.0:5001 wsgi

Now  Flask app is live,
http://18.234.210.68:5001/quote
now we can see a random motivational quote in JSON format.

{
  "quote": "Push yourself, because no one else is going to do it for you."
}
🎉 Deployment Successful!

