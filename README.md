# EX.NO:2a_Stop_and_Wait_Protocol
## NAME-SRILAKSHMI.B.H
## REG.NO-212224100057
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

client

```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server is listening...")

c, addr = s.accept()
print("Connection established with", addr)

while True:
    i = input("Enter data to send: ")
    c.send(i.encode())

    ack = c.recv(1024).decode()
    if ack:
        print("Client:", ack)
        continue
    else:
        print("No acknowledgment received. Closing connection.")
        c.close()
        break
```
server

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()
    if data:
        print("Server:", data)
        s.send("Acknowledgement Received".encode())
    else:
        print("Connection closed by server.")
        s.close()
        break
```
## OUTPUT



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
