# Web Certificates

## Generate

### [`mkcert`](https://github.com/FiloSottile/mkcert)

1. Download [`mkcert`](https://github.com/FiloSottile/mkcert/releases)
2. Rename the binary to `mkcert` and optionally, place it to `%PATH%`
3. Run `.\mkcert -install` and if on Windows Firefox do either of:
   - Go to `about:config` and set `security.enterprise_roots.enabled`
   - Go to `about:preferences#privacy`
     - Scroll to the **Certificates** section
     - Click the **View Certificates…** button
     - Switch to the **Authorities** tab
     - Click the **Import…** button
     - Locate the `rootCA.pem` file created during `mkcert -install`
     - Check **Thurst this CA to authenticate web sites**
4. Share the CA with any other computers and mobile devices that need it:
   - Computers: https://github.com/FiloSottile/mkcert#installing-the-ca-on-other-systems
   - Mobile devices: https://github.com/FiloSottile/mkcert#mobile-devices
5. Generate a certificate for your host name, e.g.: `mkcert localhost`
6. Configure your web server to use `localhost.pem` and `localhost-key.pem`

### [OpenSSL](https://gist.github.com/cecilemuller/9492b848eb8fe46d462abeb26656c4f8)

Follow the guide in the Gist.

## Use

### Node

```js
const https = require('https');
const fs = require('fs');

https.createServer(
  {
    key: fs.readFileSync('key.pem'),
    cert: fs.readFileSync('cert.pem'),
  },
  (request, response) => {
  
  },
  () => console.log('Running.')
);
```
