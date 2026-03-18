# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
Server
```
import socket

host = '127.0.0.1'
port = 5000

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((host, port))
server_socket.listen(1)

print("Server waiting for connection...")
conn, addr = server_socket.accept()
print("Connected to:", addr)

while True:
    message = conn.recv(1024).decode()
    if message.lower() == "exit":
        print("Client disconnected")
        break
    print("Client:", message)

    reply = input("Server: ")
    conn.send(reply.encode())

conn.close()
server_socket.close()

```

Client
```
import socket

host = '127.0.0.1'
port = 5000

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((host, port))

while True:
    message = input("Client: ")
    client_socket.send(message.encode())

    if message.lower() == "exit":
        break

    reply = client_socket.recv(1024).decode()
    print("Server:", reply)

client_socket.close()
```
## OUPUT
Server
<img width="1451" height="664" alt="image" src="https://github.com/user-attachments/assets/f1c98191-6693-4fca-986f-4ed401c429d7" />

Client
<img width="1420" height="420" alt="image" src="https://github.com/user-attachments/assets/374ade02-9897-4fc7-9f09-2574db9e35f4" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
