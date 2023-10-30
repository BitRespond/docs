---
layout: default
title: Contact
nav_order: 3
description: "Contact"
parent: whatsapp-sdk
permalink: /whatsapp-sdk/contact
---

## ContactModel

You can check the TypeDoc for [ContactModel]()

## Download Profile Pic

```js
if (!contact.profilePic) {
  contact.downloadProfilePic();
}
```

## Contact Presence

Presence give information about user is online, offline, typing or recording etc.
But you have to subscribe presence first.

```js
if (!user.presence) {
  await user.subscribePresence();
}

console.log(user.presence);
```

## Events

Most of time you don't need events when working with models. Because models provide these things out of the box.

```js
wa.contact.onIncoming((contacts) => {
  console.log(contacts);
});
```

### onPresenceUpdate

When user presence changes
Response: [PresenceUpdate]()

### onDownloadProfile

Response: [ContactUpdate]()

### onIncoming

Response: [ContactModel]()

### onUpdate

Response: [ContactUpdate]()