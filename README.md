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
# client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send: "))
l=list(range(size))
s=int(input("Enter Wimdow Size: "))
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
# server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())

```
## OUPUT
# client:
![2bclient](https://github.com/Ashwathm12/2b_SLIDING_WINDOW_PROTOCOL/assets/138849225/fadff310-a9f8-4e56-932d-8d7d7c0ce04e)


# server:
![2bserver](https://github.com/Ashwathm12/2b_SLIDING_WINDOW_PROTOCOL/assets/138849225/b9130cf4-b87c-4c03-8c4b-f5239e9d7cc2)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
