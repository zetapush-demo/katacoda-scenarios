You must create an account on ZetaPush platform, for this, [CONTACT US](https://www.zetapush.com/sign-up-for-a-free-trial).

After that, you will receive a login, a password, and a appName (an unique ID representing your worker on our platform).

Clone project repository and install dependencies :

`git clone https://github.com/zetapush-demo/avengers-chat.git`{{execute}}

`cd avengers-chat && npm install`{{execute}}

Repository content:
```console
.
└──
  ├── front
  │  ├── assets
  │  ├── utils
  │  ├── index.html
  │  └── index.js
  ├── worker
  │  └── index.ts (api implementation)
  └── package.json
```

Now, let's analyze the worker content.