# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## Server
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
  data = s.recv(1024).decode() 
  print(f"Received: {data}") 
```
## Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
           print(ack)
           i+=s
```
## OUPUT
![image](https://github.com/user-attachments/assets/1ce4d866-04c1-45ff-937d-726be656d490)
![image](https://github.com/user-attachments/assets/f2777cdb-7f35-4902-a0a3-2ca303eee26d)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
