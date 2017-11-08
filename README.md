# Fold
Custom binary encoding using a 67 byte charset  
Padding is enabled by default and decode is not supported without it just yet.  

The encoding can be keyed so that only the holder of the key can unlock the encoding.  Binary keys are supported.  

<<<<<<< HEAD
# Usage:  
from Fold import Fold  
Fold().encode(data)  
Fold().decode(data)  
=======
The cubesend and cuberecv methods can be used to securely transmit messages to and from a server.  They cubesend method generates a one time use 16 character key, encrypts it with the session key and then encrypts the payload with the one time key.  The cubeconnect method must be called first before using cubesend or cuberecv.

The cubeconnect utilizes a pre-shared key to exchange a random 16 character session key with the server and then proceeds using the session key.
>>>>>>> d28d219bd03d4b6eec4dc73eceda174f46015419

With keys:  

Fold(key).encode(data)  
Fold(key.decode(data)  

<<<<<<< HEAD
# Example encoding  
We hold these truths to be self-evident, that all men are created equal  
VYZaI=a=beb=Z=I=d=a=ZacfZaI=d=ceded=a=cfI=d=beI=YaZaI=cfZab=ZbLMZadfabZ=Zabdd=L=I=d=a=YZd=I=YZb=b=I=bcZabdI=YZceZaI=YbceZaYZd=ZaZ=I=ZacddeYZb=  
=======
# Prerequisites
pycube90

# Client Example

key = "Test"  
sock = CubeSocket(key)  
sock.cubeconnect("localhost", 99)  
sock.cubesend("Test")  
sock.close()  

# Server Example

host = "localhost"  
port = 99  
sock = CubeSocket("Test")  
sock.bind(host, 99)  
sock.listen(1)  
client, addr = sock.accept()  
cubesock = CubeSocket(client, sock.key)  
test = cubesock.sock.cuberecv(32)  
print test  
c.close()  
sock.close()  

# CubeWrap Example

cubesock = CubeSocket(sock, key)  
test = cubesock.sock.recv(32)  

# UDP client example

from CubeSocket import CubeSocket  

host = "localhost"  
port = 1666  

socket = CubeSocket("NEVER")  
socket.cubesendto("HELLO", host, port)  

# UDP Server example

from CubeSocket import CubeSocket

host = "localhost"  
port = 1666  

socket = CubeSocket("NEVER")  
socket.bind(host, port)  
while True:  
    data = socket.cuberecvfrom(1024)  
    print data  

# Server/Client communication using session key


host = "localhost"
sock = CubeSocket("Test", dc=0)
sock.bind(host, 99)
sock.listen(1)
client, addr = sock.accept()
cubesock = CubeSocket(client, sock.session_key)
test = cubesock.cubesock.cuberecv(32)
print test
c.close()
sock.close()

key = "Test"
sock = CubeSocket(key, dc=0)
sock.cubeconnect("localhost", 99)
sock.cubesend("Test")
sock.close()
>>>>>>> d28d219bd03d4b6eec4dc73eceda174f46015419
