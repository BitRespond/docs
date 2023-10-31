---
layout: default
title: Contact
nav_order: 3
description: "Contact"
parent: Whatsapp SM SDK
permalink: /whatsapp-sm-sdk/contact
---

## Table of contents
{: .no_toc }

1. TOC
{:toc}

---

## Use contact

```js
import {useContacts} from "whatsapp-sm-sdk";

const ContactPage = () => {
    const contacts = useContacts();

    // code...
}
```

Find a single contact
```ts
import {useFindContact} from "whatsapp-sm-sdk";

const ContactPage = ({ chatId }) => {
    const contact = useFindContact(chatId);

    // code...
}
```

## Download Profile Pic

```js
const ContactAvatar = ({ contact }) => {

    useEffect(() => {
        if (!contact.profilePic) {
            contact.downloadProfilePic();
        }
    }, []);

    return (
        <Avatar src={contact.profilePic}>{ contact.name }</Avatar>
    );
}
```

## Contact Presence

Presence give information about user is online, offline, typing or recording etc.
But you have to subscribe presence first.

```js
const ContactPresence = ({ contact }) => {

    useEffect(() => {
        if (!contact.presence) {
            contact.subscribePresence();
        }
    }, []);

    return (
        <div>({contact.presence.lastKnownPresence})</div>
    );
}
```