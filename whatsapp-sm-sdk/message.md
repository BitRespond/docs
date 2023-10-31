---
layout: default
title: Message
nav_order: 3
description: "Message"
parent: Whatsapp SM SDK
permalink: /whatsapp-sm-sdk/message
---

## Table of contents
{: .no_toc }

1. TOC
{:toc}

---

## Use messages
```js
import {useMessages} from "whatsapp-sm-sdk"

const ConversationPage = () => {
    const messages = useMessages();

    // code...
}
```

Find chat messages.
```js
import {useFindChatMessages} from "whatsapp-sm-sdk"

const ConversationPage = ({ chatId }) => {
    const messages = useFindChatMessages(chatId);

    // code...
}
```


### Text Message
[TextMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_text_message.TextMessage.html)

```js
import {TextMessage} from "whatsapp-sm-sdk"

const message = new TextMessage();
message.to = chatId;
message.text = "Sample Text message";
const id = message.send();
console.log(id);
```

### Media Message

Media message support to send image, sticker, audio, video, voice and document messages.  
[MediaMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_media_message.MediaMessage.html)

```js
// image message
const message = new MediaMessage();
message.to = chatId;
message.type = "image";
message.media = "url_to_image.jpg"; // Accept URL and local File object
message.send();

// video message
const message = new MediaMessage();
message.to = chatId;
message.type = "video";
message.media = "url_to_video.mp4"; // Accept URL and local File object
message.send();
```

### Contact Message

Send contacts. [ContactMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_contact_message.ContactMessage.html)

```js
const message = new ContactMessage();
message.to = chatId;
message.name = "Name to display";
message.phoneNumber = 16505551234;
message.send();
```

### Location Message

You can also send location message. [LocationMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_location_message.LocationMessage.html)

```js
const message = new LocationMessage();
message.to = chatId;
message.lat = 123.12;
message.lng = 53.21;
message.send();
```

### Button Message

Button message also support media message like image, video and document.
[ButtonMessage TypeDoc]({{ site.baseurl }}/typedocs/whatsapp-sdk/classes/messages_button_message.ButtonMessage.html)

```js
const message = new ButtonMessage();
message.to = chatId;
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
const message = new TemplateMessage();
message.to = chatId;
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
const message = new ListMessage();
message.to = chatId;
message.title = "List Message";
message.text = "Message body";
message.sections = [{ title: "Section 1", options: [{ title: "Option 1", description: "Option 1 description" }] }];

message.send();
```

## Reply to message

You can also reply to any message, for example we want to reply a text message to any message;

```js
const message = new TextMessage();
const message.to = chatId;
message.text = "Reply to message";
message.replyTo = message; // any existing message
message.send();
```

## Download message media

```js
const ImageMessage = ({ message }) => {

    const handleMediaDownload = () => {
        if(message.isMediaMessage()) {
            message.downloadMedia();
        }
    }

    return (
        <div>
            <img src={message.url} />
        </div>
    );
}
```

## Reply Message
If message is replied to other message

```js
const Message = ({ message }) => {

    return (
        <div>
            {message.reply && message.reply.type === "text" && <p>{message.reply.text}</p>}
        </div>
    );
}
```

## Template Message

Sometime message contain header, footer and buttons. Template contain different kind of buttons (Quick Reply, URL and Call)

```js
const Message = ({ message }) => {

    return (
        <div>
            {message.template && <p>{message.template.header}</p>}
        </div>
    );
}
```