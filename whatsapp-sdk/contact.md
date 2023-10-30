---
layout: default
title: Contact
nav_order: 3
description: "Contact"
parent: Whatsapp SDK
permalink: /whatsapp-sdk/contact
---

## Table of contents

1. TOC
{:toc}

---

## ContactModel

You can check the TypeDoc for [ContactModel](/typedocs/whatsapp-sdk/classes/models_contact_model.default.html)

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
Response: [ContactUpdate](/typedocs/whatsapp-sdk/types/events_contact_events.CBContactsUpdate.html)

### onDownloadProfile

Response: [ContactUpdate](/typedocs/whatsapp-sdk/types/events_contact_events.CBContactsUpdate.html)

### onIncoming

Response: [ContactModel](/typedocs/whatsapp-sdk/classes/models_contact_model.default.html)

### onUpdate

Response: [ContactUpdate](/typedocs/whatsapp-sdk/types/events_contact_events.CBContactsUpdate.html)
