`worker/index.ts` declare a class with which the front will interact (through ZetaPush platform) contains only 4 methods needed for our worker.

Remember what the application does :

- Ask to user which Avengers character he wants.
- Redirect to a chat with other users where he can view messages history and send new messages.

Technically, that's what our worker does :

- Create a group (if it doesn't already exist) that users can join, which represents the chat conversation.

```javascript
async createConversation() {
    const { exists } = await this.groups.exists({
        group: CONVERSATION_ID
    });

    if (!exists) {
        await this.groups.createGroup({
            group: CONVERSATION_ID
        });
    }
}
```

- Add the current user in the conversation.

```javascript
async addMeToConversation() {
    const output = await this.groups.addUser({
        group: CONVERSATION_ID,
        user: this.requestContext.owner
    });

    return output;
}
```

- Send a message on the chat and store it in database with stack service.

```javascript
async sendMessage(message = {}) {
    // Get all users inside the conversation
    const group = await this.groups.groupUsers({
        group: CONVERSATION_ID
    });
    const users = group.users || [];

    // Send the message to each user in the conversation
    this.messaging.send({
        target: users,
        channel: CHANNEL_MESSAGING,
        data: { message }
    });
    // Store the message in a stack
    await this.stack.push({
        stack: CONVERSATION_ID,
        data: message
    });
    return group;
}
```

- Get all messages in the conversation from stack service.

```javascript
async getMessages() {
    const { result } = await this.stack.list({
        stack: CONVERSATION_ID
    });

    return result;
}
```

- ... And that's all !

We put these 4 methods in a class in `worker/index.ts` :

```javascript
import { Injectable, Context } from '@zetapush/core';
import { Stack, Messaging, Groups } from '@zetapush/platform-legacy';

const CONVERSATION_ID = 'avengersChat';
const CHANNEL_MESSAGING = 'avengersChannel';

@Injectable()
export default class AvengersApi {
    private requestContext!: Context;
    constructor(
        private stack: Stack,
        private messaging: Messaging,
        private groups: Groups
    ) {}

    /* insert the 4 methods here */

}
```

In this worker class :

- requestContext is an unique ID which is used by the worker to know the caller context, to identify the client. It is injected, don't worry about its initialization.
- CONVERSATION_ID and CHANNEL_MESSAGING are constants, but we can easily turn them into variables to extend our avengers-chat.

Now, let's analyze the front content.