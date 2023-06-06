# NGINX Reverse proxy with SSL

Creating Self signed certificates using SSL

1. Create RSA private key
 > openssl genrsa -des3 -out server.key 2048
2. Create certificate signing request
 > openssl req -new -key server.key -sha256 -out server.csr
3. Generate self-signed certificate
 > openssl x509 -req -days 1825 -in server.csr -signkey server.key -sha256 -out server.crt
