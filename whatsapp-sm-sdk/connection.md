---
layout: default
title: Connection
nav_order: 1
description: "Connection"
parent: Whatsapp SM SDK
permalink: /whatsapp-sm-sdk/connection
---

## Table of contents
{: .no_toc }

1. TOC
{:toc}

---

## Connect 
First of all subscribe to events. 

```js
import {useReactSubscriber} from "whatsapp-sm-sdk";

const App = () => {
    useReactSubscriber();

    return <div>
        My Read App
    </div>
}
```

In second setup you have to connect with whatsapp server

```js
import {wa, useConnection} from "whatsapp-sm-sdk";

const LoginPage = () => {

    const connection = useConnection();

    useEffect(() => {
        if(!wa.connected){
            wa.connect("your_server_address", {
                type: "jwt",
                token: "jwt_token",
                identifier: "16505551234",
            });
        }
    }, []);

    if(connection.qr) {
        return <QR value={connection.qr} />
    }

    if(connection.state === "open") {
        return <Navigate to="/home" />
    }

    return <div>Login Page</div>
}
```