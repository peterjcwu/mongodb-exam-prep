# External Authentication Mechanisms

An external authentication mechanism does not store user credentials inside MongoDB. There are 5 types of authentication mecanisms provided by MongoDB

1. SCRAM-SHA- 1
2. MongoDB-CR
3. X.509 Certificates
4. LDAP (Lightweight Directory Access Protocal)
5. Kerberos

## SCRAM-SHA-1

The default authentication method of MongoDB

Use Challenge / Response (Username / Password)

It a IETF (internet t) Standard.

### Features

1. Evaesdropping
2. Replay
3. Database compromise
4. Maliciouse Server
   
## MongoDB-CR

MongoDB-CR is anothor Username / Password authentication method, which is replaced by SCRAM-SHA-1 and deprcated as of MongoDB 3.0

## X.509 Certificates

X.509 is the only **certificate based** authencationd method provided by MongoDB, and it's introduced in MongoDB 2.6 and required TLS connection.

## LDAP

Only provided in MongoDB Enterprise

## Kerberos

Only provided in MongoDB Enterprise
