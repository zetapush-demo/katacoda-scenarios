# Launch the application

You can launch the application locally simply by typing this command

`npm run start  -- --serve-front`{{execute}}

This command launches both a local web server on localhost:3000 and the custom cloud services on a local NodeJs. You can open a web browser on http://[[CLIENT_SUBDOMAIN]]-3000-[[KATACODA_HOST]].environments.katacoda.com/ and open the browser console.

## Modify the worker

You can modify the worker behaviour by changing the Hello World sentence by something else.

You will notice that the worker will be automagicaly reloaded and the click on the button on the front will change immediately.