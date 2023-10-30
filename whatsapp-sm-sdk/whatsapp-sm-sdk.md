---
layout: default
title: Whatsapp SM SDK
nav_order: 3
description: "Whatsapp SM SDK"
has_children: true
permalink: /whatsapp-sm-sdk
---

## Table of contents

1. TOC
{:toc}

---

### SM SDK
Whatsapp SDK with state management, we are using [zustand](https://github.com/pmndrs/zustand) as state management library.
If you are using **ReactJS** then it is recommended to use `whatsapp-sm-sdk`

### Installation

```shell
npm install whatsapp-sm-sdk
```

Installation also contain the core `whatsapp-sdk` you can access core sdk like this
```js
import {wa} from "whatsapp-sm-sdk"
```
But in most of the cases you don't need core sdk, because all these functionalities in `whatsapp-sm-sdk` are implemented in reactive way.

### Example
We have also full fledge example which implement `whatsapp-sm-sdk`, check it on GitHub.
[Whatsapp SDK Example](https://github.com/BitRespond/wa-test-frontend)

### Connection
Connect to whatsapp server, [Read more about connection](/whatsapp-sm-sdk/connection)

```js
import {wa} from "whatsapp-sm-sdk";

wa.connect("your_server_address", {
  type: "jwt",
  token: "jwt_token",
  identifier: "16505551234",
});
```

### Send Message
Here is basic example of send messages. [Read more about messages](/whatsapp-sm-sdk/message)

```js
import {TextMessage} from "whatsapp-sm-sdk"

const message = new TextMessage();
message.to = chatId;
message.text = "Sample text message";
const messageId = message.send();
console.log(messageId);
```
