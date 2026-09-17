## Computer Network Lab

**Name: Ayush Ravindra Patil**

**Roll No.: 22**

**Section: C (Batch 2)**

**Date: 17-09-26**

**Practical: 3**

### Aim: Implementation of two-way Client/Server communication using TCP Socket.

---

 <div align="right">
   <a href="https://run-python.pages.dev/bit-stuffing.html" target="_blank">
     <img src="https://img.shields.io/badge/Run_in_Live_Editor-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Run Code on My Website">
   </a>
 </div>

## **1] Server (Code)**

```python

import socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(("127.0.0.1", 8080))
server.listen(1)

print("Server is waiting for connection....")

conn, addr = server.accept()

print("Connected with: ", addr)

while True:
    client_msg = conn.recv(1024).decode()
    print("Client: ", client_msg)

    if client_msg.lower() == "exit":
        break

    reply = input("Server: ")
    conn.send(reply.encode())

    if reply.lower() == "exit":
        break

conn.close()
server.close()
```

### **Output:**

<img src="./images/image1.png"
style="" />

---

 <div align="right">
   <a href="https://run-python.pages.dev/bit-stuffing.html" target="_blank">
     <img src="https://img.shields.io/badge/Run_in_Live_Editor-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Run Code on My Website">
   </a>
 </div>

## **2] Client (Code):**

```python

import socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(("127.0.0.1", 8080))

print("Connected to Server.")

while True:
    message = input("Client: ")
    client.send(message.encode())

    if message.lower() == "exit":
        break

    reply = client.recv(1024).decode()
    print("Server: ", reply)

    if reply.lower() == "exit":
        break

client.close()
```

### **Output:**

<img src="./images/image2.png"
style="" />


<details>
  <summary><b>✨ Click here to run this code interactively</b></summary>
  <br>
  You don't need to install Python on your computer to test this assignment! 
  
  I have built a custom Cloudflare web app that lets you edit the code, enter your own inputs, and see the output live in your browser.
  
  👉 <a href="https://run-python.pages.dev/"><b>Open the Live Web Compiler</b></a>
</details>
