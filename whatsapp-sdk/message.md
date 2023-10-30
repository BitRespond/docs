---
layout: default
title: Message
nav_order: 2
description: "Message"
parent: Whatsapp SDK
permalink: /whatsapp-sdk/message
---

## MessageModel

You can check the TypeDoc for [MessageModel]()

## Display Message

```js
wa.message.onIncoming((messages) => {
  const message = messages[0];
  if (message.type === "text") {
    console.log(message.text);
  }
});
```

## Download Media

```js
wa.message.onIncoming(messages => {
    const message = messages[0];
    if(message.type === "image") {
        await message.downloadMedia();
        console.log(message.url)
    }
})
```

## Reply Message

If message is replied to other message

```js
const message = messages[0];

if (message.reply?.type === "text") {
  console.log(message.reply.text);
}
```

## Template Message

Sometime message contain header, footer and buttons. Template contain different kind of buttons (Quick Reply, URL and Call)

```js
const message = messages[0];

if (message.template) {
  console.log(message.template.header);
}
```

## Events

Most of time you don't need events when working with models. Because models provide these things out of the box.

**Example**

```js
import wa from "whatsapp-sdk";

// Subscribe to incoming message
const unsub = wa.message.onIncoming((messages) => {
  console.log(messages);
});

// Unsub when you don't need
unsub();
```

### onIncoming

When new message are received.  
Response: [MessageModel]()

### onUpdate

When any message update like when message is delivered or read by other user.  
Response: [MessageUpdate]()

### onHistory

Every time when use connect to whatsapp server, it send contacts, chats and messages.
Response: [MessageHistory]()

### onLoadMessage

When you load earlier messages.
Response: [MessageModel]()

### onMediaDownload

When you send request to download media
Response: [MessageUpdate]()
