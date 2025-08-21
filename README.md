# 5618AppliedCS-
5618
cat \${BASE_CONFIG} \\
    <(echo -e '<ca>') \\
    \${KEY_DIR}/ca.crt \\
    <(echo -e '</ca>\\n<cert>') \\
    \${KEY_DIR}/issued/\${1}.crt \\
    <(echo -e '</cert>\\n<key>') \\
    \${KEY_DIR}/private/\${1}.key \\
    <(echo -e '</key>') \\
    > \${OUTPUT_DIR}/\${1}.ovpn

journalctl -u openvpn-server@server -e

sudo openvpn --config /etc/openvpn/server/server.conf

# 创建目录
sudo mkdir -p /var/log/openvpn

# 将目录所有者更改为 openvpn 运行时使用的用户 (nobody)
sudo chown nobody:nogroup /var/log/openvpn

from socket import *

serverPort = 12000
serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', serverPort))
serverSocket.listen(1)

print('The server is ready to receive')

while 1:
    connectionSocket, addr = serverSocket.accept()
    sentence = connectionSocket.recv(1024)
    capitalizedSentence = sentence.decode().upper().encode()
    connectionSocket.send(capitalizedSentence)
    connectionSocket.close()
