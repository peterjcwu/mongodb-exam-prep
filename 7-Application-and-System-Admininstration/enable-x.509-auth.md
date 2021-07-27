# Enable X.509 Auth

## Check Mongod Supports TLS

Type <code>mongod --version</code> in the console. If you saw 
```bash
...
OpenSSL Version: 
```
which mean, the used vesion of mongod is compiled with X.509.

## Mongod Options

```bash
mongod \ 
    --sslMode requireSSL \
    --sslPEMKeyFile server.pem \ 
    --sslCAFile ca.pem
    --auth
```
(
## What's insdie the PEM file
 
 ```bash
 $ openssl x509 \
      --in client.pem \
      --info PEM \ 
      --subject \
      --nameport RFC2253 \
      --noout

$  subject= C=US, ST=New York, L=New York City, O=MongoDB, OU=KernelUser, CN=client

$  mongo --ssl --sslPEMKeyFile client.pem --sslCAFile ca.pem

mongod > db.getSiblingDB("<strong>$external</strong>").runCommand({
    createUser: "C=US, ST=New York, L=New York City, O=MongoDB, OU=KernelUser, CN=client", roles = [{role: "root", db: "admin"}]
})

 ```