# 2c.SIMULATING ARP /RARP PROTOCOLS

### NAME : PRADEEPA B
### REG NO : 212225040308
### DATE : 12/05/2026

## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP
### CLIENT SIDE
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address = {
   "165.165.80.80": "FC:6D:77:6C:39:7D",
   "165.165.79.1": "11:22:33:44:55:66"
}
while True:
   ip=c.recv(1024).decode()
   try:
      c.send(address[ip].encode())
   except KeyError:
      c.send("Not Found".encode())
```

### SERVER SIDE
```
import socket

s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```
## OUPUT -ARP
<img width="1919" height="601" alt="Screenshot 2026-05-12 111045" src="https://github.com/user-attachments/assets/d017873b-8364-4cf3-9df1-587d386aa404" />


## PROGRAM -RARP

### Client side:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","8A:BC:E3:FA":"165.165.79.1"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```
### Server side:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())

```
## OUTPUT -RARP
<img width="1919" height="458" alt="image" src="https://github.com/user-attachments/assets/5ae17cba-75f2-4760-81e6-b10519cc4edd" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
