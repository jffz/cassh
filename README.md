# admin-ssh
Easy SSH for admin ONLY !

## Prerequisites

```bash
sudo apt-get install python-psycopg2 python-webpy docker.io

mkdir test-keys
cd test-keys

ssh-keygen -C CA -f ca # without passphrase
```

Then, initialize db
```bash
# sudo is only if your user doesn't have docker rights, add it into docker group
sudo bash demo/server_init.sh
```

Finally, start server
```bash
bash demo/server_start.sh test-keys/ca
```

## Quick test

Generate key pair then sign it !

```bash
# Generate key pair
ssh-keygen -t ecdsa -f test-keys/id_rsa

# List keys (just in case... it should be '[]')
curl http://localhost:8080/client

# Add it into server
curl -X PUT -d @test-keys/id_rsa.pub http://localhost:8080/client/toto

# ADMIN: Active key
curl http://localhost:8080/admin/toto?sign=true

# Sign it !
curl -X POST -d @test-keys/id_rsa.pub http://localhost:8080/client/toto
```
The output is the signing key.

## Client CLI

```bash
# Add new key to lbcssh-server
lbcssh add <ssh pub key>

# Sign pub key
lbcssh sign <ssh pub key>

# Get public key status
lbcssh status

# Remove key from lbcssh-server
lbcssh rm <ssh pub key>

# Get ca public key
lbcssh ca

# Get ca krl
lbcssh krl
```
