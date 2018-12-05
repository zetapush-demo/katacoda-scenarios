# Introduction

<p align="center">
  <a href="https://zetapush.com/">
    <img src="https://www.zetapush.com/wp-content/uploads/2018/09/ZPlogo-websafe.png" alt="ZetaPush logo" width="200"/>
  </a>
<p>

Hello !

I will show you how to quickly create an application that allows you to use an Avengers character and chat with others.

[ZetaPush](https://www.zetapush.com/) is a back-end framework that allows you to create a serverless application using high level and remotely hosted services.

On this application, we will use 3 services :

 - [stack](https://doc.zetapush.com/#_stack) &rarr; store messages in database
 - [messaging](https://doc.zetapush.com/#_messaging) &rarr; send message on channel in realtime by websocket
 - [groups](https://doc.zetapush.com/#_groups) &rarr; create user groups

We will cover these steps:

1. Installing ZetaPush and creating a new application.
2. Developing worker API (worker is used as interaction between the ZetaPush platform and your front).
3. Writing UI and worker interaction.
4. Building your app to be deployed to production.