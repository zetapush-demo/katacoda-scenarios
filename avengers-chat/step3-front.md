With ZetaPush, you are free to implement your own UI so we won't explain how to code a message form or a messages container with HTML/CSS.

The required parts of the front are the following :

- Include ZetaPush dependencies.

```html
<!-- ZetaPush dependencies -->
<script src="https://unpkg.com/@zetapush/client"></script>
<script src="https://unpkg.com/@zetapush/platform-legacy"></script>
```

- In `index.js`, create the ZetaPush client (credentials are injected) and a ProxyTaskService to bridge with ZetaPush platform.

```js
const client = new ZetaPushClient.WeakClient();
const api = client.createProxyTaskService();
```
Now, with `api`, you can call worker-side methods (respecting its name).

For exemple : if you have a worker-side `foo()` method, just call `api.foo()` on the front side. Same way if you have a worker-side `bar(id, name)` method that take parameters, just call `api.bar(42, 'Person')`, and parameters are transmitted.

- Create service to listen incoming messages on the channel from the worker.

```js
client.createService({
    Type: ZetaPushPlatformLegacy.Messaging,
    listener: {
        /* 'channelName': yourCallbackForEachMessageReceived */
        avengersChannel: ({ data }) => controller.onAvengersMessage(data)
        /* In your code, callback is include in a 'controller' class */
    },
});
```

The callback will receive the data send by each call to `sendMessage` on the worker side, and adds a new line in the html for each received message.

- In an asynchronous function, start a connection with ZetaPush platform and call the worker methods to : create conversation (if you're the first to join the chat), add the client to this conversation, and finally get the list of messages previously sended.

```js
async onConnectionEstablished() {
    const messages = await this.api.getMessages();

    /* Add messages into the html container */

    await this.api.createConversation();
    await this.api.addMeToConversation();
}
```

- And obviously, send message when user submit the message form

```
this.api.sendMessage(message);
```