# 3b. CREATION OF CHAT USING TCP SOCKETS

**Name:** MANORAJAPRIYAN.L.E  
**Register Number:** 212225040227  
**Department:** B.E. CSE  
**College:** Saveetha Engineering College

## AIM

To write a Python program for creating Chat using TCP Sockets Links.

## ALGORITHM

1. Import the necessary modules in Python.
2. Create a socket connection using the socket module.
3. Send messages to the client and receive messages from the client using the socket module in the server.
4. Send and receive messages using the `send()` and `recv()` functions in socket.

## PROGRAM

### 1. Server Program

**File: `chat_server.py`**

```python
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

server_socket.bind((host, port))
server_socket.listen(1)

print("Waiting for client connection...")

client_socket, addr = server_socket.accept()
print("Connected to:", addr)

while True:
    client_message = client_socket.recv(1024).decode()
    print("Client:", client_message)

    if client_message.lower() == "bye":
        break

    message = input("Server: ")
    client_socket.send(message.encode())

    if message.lower() == "bye":
        break

client_socket.close()
server_socket.close()
```

### 2. Client Program

**File: `chat_client.py`**

```python
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

client_socket.connect((host, port))

print("Connected to server")

while True:
    message = input("Client: ")
    client_socket.send(message.encode())

    if message.lower() == "bye":
        break

    server_message = client_socket.recv(1024).decode()
    print("Server:", server_message)

    if server_message.lower() == "bye":
        break

client_socket.close()
```

## OUTPUT

### Server and Client Execution Output

![Chat Using TCP Sockets Output](https://github.com/user-attachments/assets/5d40056b-6832-40b8-b958-c8255d018a03)

### Sample Output

**Server Side**

```text
Waiting for client connection...
Connected to: ('127.0.0.1', 54321)

Client: Hello
Server: Hi

Client: How are you?
Server: Fine
```

**Client Side**

```text
Connected to server

Client: Hello
Server: Hi

Client: How are you?
Server: Fine
```

## HOW TO EXECUTE IN VS CODE

**Step 1:** Create two Python files:

- `chat_server.py`
- `chat_client.py`

**Step 2:** Open the first terminal and run the server.

```bash
python chat_server.py
```

**Step 3:** Open a second terminal and run the client.

```bash
python chat_client.py
```

**Step 4:** Enter messages in the client terminal and reply from the server terminal.

**Step 5:** Type `bye` to terminate the chat.

## RESULT

Thus, the Python program for creating Chat using TCP Sockets Links was successfully created and executed.
