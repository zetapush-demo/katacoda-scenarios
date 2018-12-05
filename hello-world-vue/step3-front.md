### The integration of ZetaPush is really light.

```console
npm install @zetapush/client
```

Import `WeakClient` into your Vue component.

At component initialization in its lifecycle, create `WeakClient` (credentials are injected), and a ProxyTaskService to bridge with ZetaPush platform.

```js
import { WeakClient } from '@zetapush/client';

export default {
  name: 'HelloWorld',
  methods: {
    onClick: async function() { /* called on button click */
      console.log(await this.api.hello());
    }
  },
  created: function () { /* called at component initialization */
    this.client = new WeakClient();
    this.api = this.client.createProxyTaskService();

    this.client.connect().then(() => {
      document.getElementById('main').classList.add('connected')
    });
  }
}
```

On button click, call `onClick()` method to invoke your worker method.

```html
<button v-on:click="onClick()">call hello()</button>
```