---
layout: post
title:  "How to create a https websocket node server"
date:   2019-09-24 10:58:00 -0500
categories: [programming, js]
permalink: How-to-create-a-https-websocket-node-server
---

I created a [similar post](https://mason.github.io/How-to-create-a-https-node-server) regarding a vanilla https node server. It references links that are useful in [understanding SSL](https://www.youtube.com/watch?v=T4Df5_cojAs) and [OpenSSL req command](https://www.openssl.org/docs/man1.0.2/man1/openssl-req.html).

Just like in the previous post, we need to create the private key and certificate.
```
openssl req -x509 -newkey rsa:2048 -keyout priv.key -out cert.csr -days 100 -nodes
```

First, initialize npm so we can install some libraries: `npm init`.
Next run `npm install ws` to get the websocket dependency. 

Create the node js file that will bootstrap the node server. This file will reference the certificate and private key.

{% highlight js %}
'use strict';
const fs = require('fs'),
      https = require('https'),
      WebSocket = require('ws');

const httpsServer = https.createServer({
  key: fs.readFileSync('priv.key', 'utf8'),
  cert: fs.readFileSync('cert.csr', 'utf8')
});

const wss = new WebSocket.Server({
  server: httpsServer
});

httpsServer.on('request', (req, res) => {
  res.writeHead(200);
  res.end('hello world...');
});

wss.on('connection', function connection(connection) {
  connection.on('message', function incoming(message) {
    console.log("received message: " + message);
    connection.send(message);
  });
});

httpsServer.listen(8000);
{% endhighlight %}

Start the node server by running `node index.js`.

Next visit `https://127.0.0.1:8000`. Your browser should complain about the self signed certificate but just click accept and continue.

Finally open up js console in the browser and create the websocket `ws = new WebSocket('wss://127.0.0.1:8000');`. **IMPORTANT NOTE**: the url used in the `wss://<url>` must match the url in the web browser. So in this example, it can't be `ws = new WebSocket('wss://localhost:8000');`. Doing so may result in `ERR_CERT_AUTHORITY_INVALID` error when trying to establish a connection to the websocket.
 
 Send over a message using this command on the js console: `ws.send("hello world");` and check the server output from the terminal foreground. It should echo back `hello world`.






