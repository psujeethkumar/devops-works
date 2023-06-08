# NGINX Reverse proxy with SSL

Creating Self signed certificates using SSL

1. Create RSA private key
```
openssl genrsa -des3 -out server.key 2048 
```
2. Create certificate signing request
``` 
openssl req -new -key server.key -sha256 -out server.csr 
```
3. Generate self-signed certificate
``` 
openssl x509 -req -days 1825 -in server.csr -signkey server.key -sha256 -out server.pem 
```


NGNIX Configuration file

Config file for NGNIX server operating in a reverse proxy and accepting only HTTPS traffic :

``` Linux
#Server configuration for HTTPS traffic
server {
    access_log /var/log/nginx/service_access_https.log main;

    listen 7843 ssl;
    server_name SERVER-HOST-NAME;


    # TLS config
    #ssl on;
    ssl_certificate server.pem; # Provide the absolute path of the certificate generated using openssl
    ssl_certificate_key  server.key; # provide the absolute path of the certificate private key file which is generated using openssl
    #ssl_session_cache
    #ssl_session_timeout
    #ssl_ciphers
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;

    # API/Service definitions, one per file
    include services_conf.d/*_https.conf;

    # Error responses
    error_page 404 = @400;         # Treat invalid paths as bad requests
    proxy_intercept_errors on;     # Do not send backend errors to client
    #include api_json_errors.conf;  # API client-friendly JSON errors
    #default_type application/json; # If no content-type, assume JSON
}
```
Test & reload the nginx server

``` Linux
nginx -t
nginx -s reload
```
