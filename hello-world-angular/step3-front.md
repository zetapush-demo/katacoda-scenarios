The integration of ZetaPush is really light.

`src` is a basic Angular application.

`src/app/app.component.ts` is the main component, with worker interaction.

At component constructor, create `WeakClient` (credentials are injected), and a ProxyTaskService to bridge with ZetaPush platform.

```js
export class AppComponent implements OnInit {

  client: WeakClient;
  api: ProxyTaskService;

  async onClick() {
    console.log(await this.api.hello());
  }

  async ngOnInit() {
    this.client = new WeakClient({
      appName: 'willBeInject'
    });
    this.api = this.client.createProxyTaskService();
    this.client.connect().then(() =>
      document.getElementById('main').classList.add('connected')
    );
  }
}
```

On button click, call `onClick()` method to invoke your worker method.

`<button class="js-Hello" (click)="onClick()">call hello()</button>`