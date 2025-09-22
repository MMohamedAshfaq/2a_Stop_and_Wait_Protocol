# 2a_Stop_and_Wait_Protocol
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
Client:
```
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Waiting for server to connect...")
c, addr = s.accept()
print("Connected to:", addr)
while True:
    i = input("Enter a data: ")
    if not i:
        print("No input. Closing connection.")
        c.close()
        break
    c.send(i.encode())
    ack = c.recv(1024).decode()
    if ack:
        print("Received from server:", ack)
        continue
    else:
        print("No ACK received. Closing connection.")
        c.close()
        break
```
Server:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()
    if not data:
        print("No data received. Closing connection.")
        s.close()
        break

    print("Received from client:", data)
    s.send("ACK".encode())
```

## OUTPUT:
Client:
<img width="2198" height="1206" alt="Screenshot 2025-09-22 113047" src="https://github.com/user-attachments/assets/1c389fb2-acba-42f5-a363-b7452fb607eb" />
Server:
<img width="2328" height="1204" alt="Screenshot 2025-09-22 112926 server" src="https://github.com/user-attachments/assets/c95374f4-a3ca-41fe-867f-b4a0204db84f" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
