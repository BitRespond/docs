---
layout: default
title: Connection
nav_order: 1
description: "Connection"
parent: Whatsapp SDK
permalink: /whatsapp-sdk/connection
---

## Table of contents

1. TOC
{:toc}

---

## ConnectionModel

You can check the TypeDoc for [ConnectionModel](/typedocs/whatsapp-sdk/classes/models_connection_model.default.html)

## Connection

Get server address from BitRespond, If you do not setup your whatsapp server contact with BitRespond.
Here is how you can connect with whatsapp server. You need three things to connect with server.

1. Server address
1. Token (static or jwt) it will authenticate user, for client side connection we recommend to use jwt for better security
1. Identifier, you can use anything for identifier. Identifier differentiate each user connection. We recommend to use phone number as identifier but
   you can any `string` that contain Alphabetic and numbers.

```js
import wa from "whatsapp-sdk";

wa.connect('your_server_address', {
    type: "jwt" // It can be static or jwt token
    token: "jwt_token",
    identifier: "16505551234"
});

// QR code when user to connect first time
wa.connection.onUpdate(conn => {
    console.log(conn.qr)
})
```

It will connect with whatsapp if connection is not exist a QR code will return and user have to scan this QR code from their mobile. If connection
already exist then you will automatically connect with whatsapp server, no need to scan QR code each time. SDK remember each connection state and
reconnect if any connection lost.

## Core Socket

You can also get the core socket, we use `socket.io` under the hood.

```js
wa.socket.on();

wa.socket.emit();
```

## Events

```js
wa.connection.onError((err) => {
  console.log(err);
});
```

### onError

When any error occur.
Response: `string`

### onConnectError

When error occur on connection time, for example authentication fail etc.
Response: `string`

### onConnect

When connection successfully established.
Response: `void`

You can also check if SDK is connected or not by using `connected` property.

```js
if (wa.connected) {
  // do something
}
```

### onUpdate

When whatsapp connection update, response also contain QR code when first time user connect to whatsapp.
Response: [ConnectionModel](/typedocs/whatsapp-sdk/classes/models_connection_model.default.html)
