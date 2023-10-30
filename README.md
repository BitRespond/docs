<p>
    <h1 align="center">Whatsapp SDK</h1>
    <p align="center">
       Whatsapp SDK allow you to communicate with whatsapp services, just install and use. There are two types of SDKs one is
        core `whatsapp-sdk` and other one is core sdk with state management which is useful for React like application `whatsapp-sm-sdk`
    </p>
    <p align="center">
        <strong>
            <a href="https://ws-docs.bitrespond.com">Get Started!</a>
        </strong>
    </p>
    <br><br><br>
</p>

## Installation

```shell
npm install whatsapp-sdk
```

or for ReactJS

```shell
npm install whatsapp-sm-sdk
```

## React Example usage

First of all subscribe to events.

```js
import { useReactSubscriber } from "whatsapp-sm-sdk";

const App = () => {
  useReactSubscriber();

  return <div>My Read App</div>;
};
```

In second setup you have to connect with whatsapp server

```js
import { wa, useConnection } from "whatsapp-sm-sdk";

const LoginPage = () => {
  const connection = useConnection();

  useEffect(() => {
    if (!wa.connected) {
      wa.connect("your_server_address", {
        type: "jwt",
        token: "jwt_token",
        identifier: "16505551234",
      });
    }
  }, []);

  if (connection.qr) {
    return <QR value={connection.qr} />;
  }

  if (connection.state === "open") {
    return <Navigate to="/home" />;
  }

  return <div>Login Page</div>;
};
```

## Example usage with core SDK

```js
import wa from "whatsapp-sdk";

wa.connect("your_server_address", {
  type: "jwt",
  token: "jwt_token",
  identifier: "16505551234",
});

// QR code when user to connect first time
wa.connection.onUpdate((conn) => {
  console.log(conn.qr);
});
```

Here is basic example of listing incoming and send messages.

```js
// Subscribe to incoming message
wa.message.onIncoming((messages) => {
  console.log(messages);
});

// Send message
const message = new wa.message.send.text();
message.to = send_to_id;
message.text = "Sample text message";
const messageId = message.send();
console.log(messageId);
```
