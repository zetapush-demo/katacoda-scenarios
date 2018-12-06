You must create an account on ZetaPush platform, for this, [CONTACT US](https://www.zetapush.com/sign-up-for-a-free-trial).

After that, you will receive a login, a password, and a appName (an unique ID representing your worker on our platform).

Clone project repository and install dependencies :

`git clone https://github.com/zetapush/zetapush-examples.git --no-checkout`{{execute}}

`cd zetapush-examples && git checkout HEAD hello-world/hello-world-angular`{{execute}}

`cd hello-world/hello-world-angular && npm install`{{execute}}

Project structure:
```console
.
└──
  ├── src (Angular application)
  ├── worker
  │  └── index.ts (api implementation)
  ├── angular.json
  └── package.json
```

Now, let's analyze the worker content.