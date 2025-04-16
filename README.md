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
Client
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
Server
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
Client
![image](https://github.com/user-attachments/assets/417d708a-6aa6-48d6-8e14-b59fb0606262)
server
![image](https://github.com/user-attachments/assets/158c0438-aee5-4c5e-96a6-670c3dfeb085)


## PROGRAM - RARP
Client
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
Server
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
Client
![image](https://github.com/user-attachments/assets/e255645e-1d3f-4bda-af30-4741f4446c0f)
server
![image](https://github.com/user-attachments/assets/a6a3fd24-b679-494e-a837-c6936d07e59c)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
