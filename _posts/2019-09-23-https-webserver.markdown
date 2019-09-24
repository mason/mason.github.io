---
layout: post
title:  "How to create a https node server"
date:   2019-09-23 14:56:50 -0500
categories: [programming, js]
permalink: How-to-create-a-https-node-server
---
It's always good to have a basic understanding of how SSL works. I recommend [this video](https://www.youtube.com/watch?v=T4Df5_cojAs) 

First we need to make the server certificate and server private key. The certificate contains the server public key that the client will use for the secret key exchange. The server private key is what the server uses to decrypt anything encrypted with the server public key (In this case the encrypted secret key from the client)

```
openssl req -x509 -newkey rsa:2048 -keyout myserver.key -out cert.csr -days 100 -nodes
```
Provide the necessary information from the command. For details on these options. Please see [openssl req docs](https://www.openssl.org/docs/man1.0.2/man1/openssl-req.html)


Create the node js file that will bootstrap the node server. This file will reference the certificate and private key.

{% highlight js %}
'use strict';
const fs = require('fs'),
      https = require('https');

const httpsServer = https.createServer({
  key: fs.readFileSync('myserver.key'),
  cert: fs.readFileSync('cert.csr')
});

httpsServer.on('request', (req, res) => {
  res.writeHead(200);
  res.end('hello world');
});


httpsServer.listen(8080, '127.0.0.1', () => {
  console.log('Server running...');
});
{% endhighlight %}

next visit `https://127.0.0.1:8080`. Your browser should complain about the self signed certificate but just click accept and continue. You should see `hello world` on the page and the url bar should show https with a broken lock(due to self signed cert).





