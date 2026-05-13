# 2c.SIMULATING ARP /RARP PROTOCOLS
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
P
## PROGRAM - ARP
CLient program
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
       ip=c.recv(1024).decode()
       try:
          c.send(address[ip].encode())
       except KeyError:
          c.send("Not Found".encode())
 ```
server program
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```        
## OUPUT - ARP
<img width="1032" height="270" alt="Screenshot 2026-05-13 103534" src="https://github.com/user-attachments/assets/bfeb66a8-f80d-4876-8947-b390b0869969" />
<img width="999" height="28" alt="Screenshot 2026-05-13 103732" src="https://github.com/user-attachments/assets/109cb2a5-3f39-48fe-9a4d-b371cbb4f62d" />

## PROGRAM - RARP
client program
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
server program
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
ip=input("Enter MAC Address : ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP
<img width="1129" height="108" alt="Screenshot 2026-05-13 105840" src="https://github.com/user-attachments/assets/82262899-3dba-424c-921b-de8f31c954a7" />
<img width="836" height="86" alt="Screenshot 2026-05-13 105935" src="https://github.com/user-attachments/assets/577b17a6-fa61-4fe6-80f8-a1e0c0580d4a" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
