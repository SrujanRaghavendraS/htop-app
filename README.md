from flask import Flask
import getpass
import subprocess
from datetime import datetime
import pytz

app = Flask(__name__)

@app.route('/htop')
def htop():
    name = "Srujan Raghavendra S"
    username = getpass.getuser()
    ist_time = datetime.now(pytz.timezone('Asia/Kolkata'))
    top_output = subprocess.getoutput("top -b -n 1 | head -20")
    return f"<h2>Name: {name}</h2><h3>Username: {username}</h3><h3>Server Time (IST): {ist_time}</h3><pre>{top_output}</pre>"

@app.route('/')
def test():
    return "Please Navigate to /htop for the result"
    
if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
