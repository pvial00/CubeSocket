# CubeSocket
Socket bindings using the Cube90 cipher for encryption and decryption

# Description
CubeSocket provides two classes CubeSocket and CubeWrap.  CubeSocket is used like the ordinary socket calls but the are encapsulated with the Cube90 cipher.  CubeWrap is used to encapulate an existing socket.

The cubeconnect method utilizes a pre-shared key to exchange a random 16 character session key with the server and then proceeds using the session key.

A socket can be utilized directly without a secure handshake by calling CubeSocket's connect method.  The key must be known on either end.

Supports ASCII characters 32-90

# Prerequisites
pycube90

# Client Example
key = "Test"
sock = CubeSocket(key)
sock.cubeconnect("localhost", 99)
sock.send("Test")
sock.close()

# Server Example
host = "localhost"
port = 99
sock = CubeSocket("Test")
sock.bind(host, 99)
sock.listen(1)
client, addr = sock.accept()
cubesock = CubeWrap(client, sock.key)
test = cubesock.sock.recv(32)
print test
c.close()
sock.close()

# CubeWrap Example
cubesock = CubeWrap(sock, key)
test = cubesock.sock.recv(32)
