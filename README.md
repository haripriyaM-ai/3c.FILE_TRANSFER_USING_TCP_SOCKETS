# Exp: 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

### client.py
```python
import socket

s = socket.socket()
s.connect((socket.gethostname(), 60000))
s.send(b"Hello server!")

with open('received_file', 'wb') as f:
    while True:
        d = s.recv(1024)
        if not d:
            break
        print('Receiving', d)
        f.write(d)

s.close()
print('Done')
```

### server.py
```python
import socket

s = socket.socket()
s.bind((socket.gethostname(), 60000))
s.listen(5)

while True:
    c, a = s.accept()
    msg = c.recv(1024)
    print("Received:", msg)
    
    with open('mytext.txt', 'rb') as f:
        while True:
            d = f.read(1024)
            if not d:
                break
            c.send(d)
    
    c.send(b'Thank you')
    c.close()
```

## OUPUT
<img width="1481" height="1004" alt="image" src="https://github.com/user-attachments/assets/342a5052-75ff-4937-a29c-9b6f510203e3" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
