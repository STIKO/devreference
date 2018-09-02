##Show Public SSL Certificate
This command will show you the certificate (use -showcerts as an extra parameter if you want to see the full chain):
```bash
openssl s_client -connect the.host.name:443
```
This will get the certificate and print out the public key:
```bash
openssl s_client -connect the.host.name:443 | openssl x509 -pubkey -noout
```

