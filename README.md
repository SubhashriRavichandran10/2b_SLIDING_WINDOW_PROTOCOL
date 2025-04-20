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

CLIENT.py

```

import socket
s=socket.socket()
s.bind(("localhost",8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter the number of frames to send :"))
l=list(range(size))
s=int(input("Enter the Window Size : "))
st=0
i=0
while (i<len(l)):
    st+=s
    c.send(str(l[i:st]).encode())
    ack=c.recv(1024).decode()
    if ack:
        print(ack)
        i+=s



```


SERVER.py

```


import socket
s=socket.socket()
s.connect(("localhost",8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())

```

## OUPUT

CLIENT.py

![image](https://github.com/user-attachments/assets/bbd1f7e2-4ad6-4d39-84e1-24f9e8cb1adc)




SERVER.py

![image](https://github.com/user-attachments/assets/238ce3a0-8eef-4f03-a528-f9ab19ff717b)



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
