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
client
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
server
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:    
 print(s.recv(1024).decode()) 
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
client
![Screenshot 2025-04-16 201626](https://github.com/user-attachments/assets/83220ae6-3975-41ac-bb3d-12ac0ab12d5c)
server
![Screenshot 2025-04-16 201642](https://github.com/user-attachments/assets/6d1a651e-8a0f-4b0f-8fc3-4f699c137d9e)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
