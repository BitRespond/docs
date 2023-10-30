---
layout: default
title: Chat
nav_order: 4
description: "Chat"
parent: Whatsapp SDK
permalink: /whatsapp-sdk/chat
---

## Table of contents

1. TOC
{:toc}

---

## ChatModel

You can check the TypeDoc for [ChatModel](/typedocs/whatsapp-sdk/classes/models_chat_model.default.html)

## Last Message

Most of the time chats contain last message if not then you load load last message

```js
if (!chat.lastMessage) {
  await chat.getLastMessage();
}

console.log(chat.lastMessage);
```

## Load Earlier Message

```js
await chat.loadEarlierMessages(); // By default load 50 message

// Load more 50 older message
await chat.loadEarlierMessages();
```

## Load Messages

You can set custom limit to load messages.

```js
await chat.loadMessages({ skip: 50, limit: 100 });
```

## Mark chat as read

```js
await chat.markAsRead();
```

## Events

Most of time you don't need events when working with models. Because models provide these things out of the box.

### onLastMessage

Response: [ChatUpdate](/typedocs/whatsapp-sdk/types/events_chat_events.CBChatUpdate.html)

### onIncoming

Response: [ChatModel](/typedocs/whatsapp-sdk/classes/models_chat_model.default.html)

### onUpdate

Response: [ChatUpdate](/typedocs/whatsapp-sdk/types/events_chat_events.CBChatUpdate.html)

### onDelete

Response: `string[]`
