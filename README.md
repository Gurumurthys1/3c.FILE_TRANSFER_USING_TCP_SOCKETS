# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

### Server
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server listening on port", port)
while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = r'C:\Users\admin\Desktop\folder_for_me\OneDrive\Documents\computer_nutwork\exp_no_7\myfile.txt'
    with open(filename, 'rb') as f:
        chunk = f.read(1024)
        while chunk:
            conn.send(chunk)
            print('Sent', repr(chunk))
            chunk = f.read(1024)

    print('Done sending')
    conn.send("Thank you for connecting".encode())
    conn.close()

```

### Client:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file.txt', 'wb') as f:
    print('Receiving data...')
    while True:
        data = s.recv(1024)
        if not data:
            break
        f.write(data)
print('Successfully received the file')
s.close()
print('Connection closed')

```
### text file:
![image](https://github.com/user-attachments/assets/6476861f-ac2c-49c4-96a2-511a7680c7a1)

## OUPUT
### Server:
![image](https://github.com/user-attachments/assets/6b9e200e-d3e5-4ede-9699-737dc8799936)
### Client:
![image](https://github.com/user-attachments/assets/85f05179-325f-4bb2-8a6c-f686d99035f5)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
