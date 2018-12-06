`worker/index.ts` declare a class with which the front will interact (through ZetaPush platform).

This class expose an method called `hello()` which returns a string "Hello World from Worker" concatened with server timestamp :

```js
export default class Api {
  hello() {
    return `Hello World from Worker ${Date.now()}`;
  }
}
```

Now, let's analyze the front content.