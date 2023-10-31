---
layout: default
title: Global
nav_order: 5
description: "Global"
parent: Whatsapp SDK
permalink: /whatsapp-sdk/global
---

## Table of contents
{: .no_toc }

1. TOC
{:toc}

---

We don't not provide any webhooks but you can use **global** instance of sdk to listen events in any identifier.
For example you can check when new message arrive or new chat start etc. Here is [Supported Global Events]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/whatsapp_client.default.html#global)

## Connection
You can use any existing connection with `joinGlobal` flag. Then you can also listen to global events.

```js
import wa form "whatsapp-sdk";

wa.connect('your_server_address', {
    type: "static",
    token: "static_token",
    identifier: "16505551234",
    joinGlobal: true
});
```

Or you can only connect as a global instance, You can't perform other operation in global instance like send messages etc.
Global instance only use to listen global events in any identifier.

```js
import wa form "whatsapp-sdk";

wa.connect('your_server_address', {
    type: "static",
    token: "static_token",
    identifier: "global", // global is special identifier
});
```

## Events
Each global event contains `identifier` in its first parameter, so you can easily identify from where this data is coming.
Here is list of [Supported Global Events]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/whatsapp_client.default.html#global)

### onMessageIncoming

```js
const unsub = wa.global.onMessageIncoming((identifier, messages) => {
    console.log(identifier, messages)
})

// Unsubscribe when no need
unsub();
```

### onMessageUpdate

### onNewChat

### onChatUpdate

### onConnectionUpdate

### onNewContact

### onContactUpdate