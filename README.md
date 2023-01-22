### Before forking/ cloning 
Create a folder called certs and run the following command to generate a self-signed certificate and change the server to redirect to HTTPS.

```
openssl req -x509 -out localhost.crt -keyout localhost.key \
  -newkey rsa:2048 -nodes -sha256 \
  -subj '/CN=localhost' -extensions EXT -config <( \
   printf "[dn]\nCN=localhost\n[req]\ndistinguished_name = dn\n[EXT]\nsubjectAltName=DNS:localhost\nkeyUsage=digitalSignature\nextendedKeyUsage=serverAuth")
```
#### Steps: 
1) Run `npm install`

2) If you are using VS Code, open index.html and click `Go Live` to run on the port. 

3) Open chrome dev tools to see if service worker is 3) registered and try to click offline too! 
   
4) Run the Lighhouse tool. PWA should be able to install and it passes the audit checks.

### Screenshots:

Install Icon:
![Screenshot1](https://github.com/sdkdeepa/GeekleNodeJS2023/blob/main/screenshots/installIcon.png)

Manifest:
![Screenshot2](https://github.com/sdkdeepa/GeekleNodeJS2023/blob/main/screenshots/manifest.png)

PWA Lighthouse Audit:
![Screenshot3](https://github.com/sdkdeepa/GeekleNodeJS2023/blob/main/screenshots/PWApassesWithSWregistered.png)
