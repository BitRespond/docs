---
layout: default
title: Message
nav_order: 2
description: "Message"
parent: Whatsapp SDK
permalink: /whatsapp-sdk/message
---

## Table of contents

1. TOC
{:toc}

---

## Send Message

You can send different types of messages, text, audio, video, image, stick, list, buttons and template message. We support all types of message to send.
You can check type docs to see what kind of message are support to send. [Send Message TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/whatsapp_client.default.html#message)

### Text Message
[TextMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_text_message.TextMessage.html)

```js
const message = new wa.message.send.text();
message.to = send_to_id;
message.text = "Sample Text message";
const id = message.send();
console.log(id);
```

### Media Message

Media message support to send image, sticker, audio, video, voice and document messages.  
[MediaMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_media_message.MediaMessage.html)

```js
// image message
const message = new wa.message.send.media();
message.to = send_to_id;
message.type = "image";
message.media = "url_to_image.jpg"; // Accept URL and local File object
message.send();

// video message
const message = new wa.message.send.media();
message.to = send_to_id;
message.type = "video";
message.media = "url_to_video.mp4"; // Accept URL and local File object
message.send();
```

### Contact Message

Send contacts. [ContactMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_contact_message.ContactMessage.html)

```js
const message = new wa.message.send.contact();
message.to = send_to_id;
message.name = "Name to display";
message.phoneNumber = 16505551234;
message.send();
```

### Location Message

You can also send location message. [LocationMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_location_message.LocationMessage.html)

```js
const message = new wa.message.send.location();
message.to = send_to_id;
message.lat = 123.12;
message.lng = 53.21;
message.send();
```

### Button Message

Button message also support media message like image, video and document.
[ButtonMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_button_message.ButtonMessage.html)

```js
const message = new wa.message.send.button();
message.to = send_to_id;
message.type = "text";
message.text = "Text with buttons";
message.buttons = ["Btn 1", "Btn 2", "Btn 3"];
message.send();
```

### Template Message

Template messages are similar to button message but provide more control on buttons.
You can send different kind of buttons, like Quick Reply, URL and call type buttons, you can add up to three buttons in template message.
Template message also support media like button message.  
[TemplateMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_template_message.TemplateMessage.html)

```js
const message = new wa.message.send.template();
message.to = send_to_id;
message.type = "text";
message.text = "Text with template message";
message.buttons = [
  { type: "reply", text: "Quick Reply" },
  { type: "url", text: "http://bitrespond.com" },
];

message.send();
```

### List Message

List message provide user to select from multiple options.  
[ListMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_list_message.ListMessage.html)

```js
const message = new wa.message.send.list();
message.to = send_to_id;
message.title = "List Message";
message.text = "Message body";
message.sections = [{ title: "Section 1", options: [{ title: "Option 1", description: "Option 1 description" }] }];

message.send();
```

## Reply to message

You can also reply to any message, for example we want to reply a text message to any message;

```js
const message = new wa.message.send.text();
const message.to = send_to_id;
message.text = "Reply to message";
message.replyTo = message; // any existing message
message.send();
```

## MessageModel

You can check the TypeDoc for [MessageModel]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/models_message_model.default.html)

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
Response: [MessageModel]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/models_message_model.default.html)

### onUpdate

When any message update like when message is delivered or read by other user.  
Response: [MessageUpdate]({{ site.baseurl }}/typedocs/whatsapp-sdk/types/events_message_events.CBMessageUpdate.html)

### onHistory

Every time when use connect to whatsapp server, it send contacts, chats and messages.
Response: [MessageHistory]({{ site.baseurl }}/typedocs/whatsapp-sdk/types/events_message_events.CBMessageHistory.html)

### onLoadMessage

When you load earlier messages.
Response: [MessageModel]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/models_message_model.default.html)

### onMediaDownload

When you send request to download media
Response: [MessageUpdate]({{ site.baseurl }}/typedocs/whatsapp-sdk/types/events_message_events.CBMessageUpdate.html)
