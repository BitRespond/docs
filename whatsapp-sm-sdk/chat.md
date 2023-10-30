---
layout: default
title: Chat
nav_order: 2
description: "Chat"
parent: Whatsapp SM SDK
permalink: /whatsapp-sm-sdk/chat
---

## Table of contents

1. TOC
{:toc}

---

## Use Chats
```js
import {useChats} from "whatsapp-sm-sdk";

const ChatPage = () => {
    const chats = useChats();

    // code...
}
```

Find a single chat.
```js
import {useFindChat} from "whatsapp-sm-sdk";

const ChatPage = ({ chatId }) => {
    const chat = useFindChat(chatId);

    // code...
}
```


## Last Message

Most of the time chats contain last message if not then you load last message

```js
const ConversationPage = ({ chat }) => {
    useEffect(() => {
        if(!chat.lastMessage) {
            chat.getLastMessage()
        }
    }, [])

    return (
        <div>
            last Message:  {JSON.stringify(chat.lastMessage)}
        </div>
    );
}
```

## Load Earlier Message

```js
const MessagesPage = ({ chat }) => {
    const messages = useFindChatMessages(chat.id);

    useEffect(() => {
        if(!message?.length) {
            chat.loadEarlierMessages();
        }
    }, []);

    // When use reach at the top then load more older messages
    useEffect(() => {
        if(scrollIsOnTop) {
            chat.loadEarlierMessages();
        }
    }, []);

    // code...
}
```

## Load Messages

You can set custom limit to load messages.

```js
const MessagesPage = ({ chat }) => {
    const messages = useFindChatMessages(chat.id);

    useEffect(() => {
        chat.loadMessages({ skip: 50, limit: 100 })
    }, []);

    // code...
}
```

## Mark chat as read

```js
const ChatPage = ({ chat }) => {
    
    useEffect(() => {
        if (chat?.unreadCount && chat.unreadCount > 0) {
            chat.markAsRead();
        }
    }, []);

    return <div>
        unread count: {chat.unreadCount}
    </div>
}
```