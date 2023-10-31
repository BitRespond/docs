---
layout: default
title: Whatsapp SDK
nav_order: 2
description: "Whatsapp core SDK"
has_children: true
permalink: /whatsapp-sdk
---

## Table of contents

1. TOC
{:toc}

---

# Core SDK

Core SDK can be use on client side as well as on nodeJs as a backend service

### Installation

```shell
npm install whatsapp-sdk
```

### Connection

Connect to whatsapp server, [Read more about connection](whatsapp-sdk/connection)

```js
import wa from "whatsapp-sdk";

wa.connect("your_server_address", {
  type: "jwt",
  token: "jwt_token",
  identifier: "16505551234",
});

// QR code when user to connect first time
wa.connection.onUpdate((conn) => {
  console.log(conn.qr);
});
```

### Messages

Here is basic example of listing incoming and send messages. [Read more about messages](/whatsapp-sdk/message)

```js
// Subscribe to incoming message
wa.message.onIncoming((messages) => {
  console.log(messages);
});

// Send message
const message = new wa.message.send.text();
message.to = send_to_id;
message.text = "Sample text message";
const messageId = message.send();
console.log(messageId);
```
