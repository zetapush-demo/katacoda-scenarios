You must create an account on ZetaPush platform, for this, [CONTACT US](https://www.zetapush.com/sign-up-for-a-free-trial).

After that, you will receive a login, a password, and a appName (an unique ID representing your worker on our platform).

Clone project repository and install dependencies :

`git clone https://github.com/zetapush/zetapush-examples.git --no-checkout`{{execute}}

`cd zetapush-examples && git checkout HEAD hello-world/hello-world-react`{{execute}}

`cd hello-world/hello-world-react && (npm install && cd src && npm install)`{{execute}}

Project structure:
```console
.
└──
  ├── src (react application)
  │  ├── src
  │  ├── public
  │  ├── package.json
  ├── worker
  │  └── index.ts (api implementation)
  └── package.json
```

Now, let's analyze the worker content.