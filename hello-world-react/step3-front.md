The integration of ZetaPush is really light.

`src` is a basic React.js application.

`src/App.js` is the main component, with worker interaction.

At component constructor, create `WeakClient` (credentials are injected), and a ProxyTaskService to bridge with ZetaPush platform.

```js
class App extends Component {

  constructor() {
    super()
    this.onClick = this.onClick.bind(this);

    this.client = new WeakClient();
    this.api = this.client.createProxyTaskService();
    this.client.connect().then(() => {
      document.getElementById('main').classList.add('connected')
    });
  }

  async onClick() { /* called on button click */
    console.log(await this.api.hello());
  }

  render() {
    return (
      /* at least a button with "onClick={this.onClick}" */
    );
  }
}
```

On button click, call `onClick()` method to invoke your worker method.
`<button className="js-Hello" onClick={this.onClick}>call hello()</button>`