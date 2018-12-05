You must create an account on ZetaPush platform, for this, [CONTACT US](https://www.zetapush.com/sign-up-for-a-free-trial).

After that, you will receive a login, a password, and a appName (an unique ID representing your worker on our platform).

Clone project repository and install dependencies :

`git clone https://github.com/zetapush/zetapush-examples.git --no-checkout`{{execute}}

`git checkout HEAD hello-world/hello-world-vue`{{execute}}

`cd hello-world/hello-world-vue && npm install`{{execute}}

Project structure:
```console
.
└──
  ├── public (Vue.js public folder)
  │  └── index.html
  ├── src (Vue.js application)
  │  ├── components
  │  │	└── HelloWorld.vue
  │  ├── assets
  │  ├── App.vue
  │  └── main.js
  ├── worker
  │  └── index.ts (api implementation)
  └── package.json
```

Now, let's analyze the worker content.