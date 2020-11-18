# Readings: HEROKU
## Read:05 - Heroku Deployment

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-05).

### For this class, I will be reading from this resource: `Heroku: Getting Started with Node`.

### :pushpin: [Heroku: Getting Started with Node](https://devcenter.heroku.com/articles/getting-started-with-nodejs)


## View logs

Heroku treats logs as streams of time-ordered events aggregated from the output streams of all your app and Heroku components, providing a single channel for all of the events.

View information about your running app using one of the logging commands, heroku logs --tail:

![](heroku.png)

Press Control+C to stop streaming the logs.

## Define a Procfile
Use a Procfile, a text file in the root directory of your application, to explicitly declare what command should be executed to start your app.

The Procfile in the example app you deployed looks like this:
```
    web: node index.js
```
This declares a single process type, web, and the command needed to run it. The name web is important here. It declares that this process type will be attached to the HTTP routing stack of Heroku, and receive web traffic when deployed.

Procfiles can contain additional process types. For example, you might declare one for a background worker process that processes items off of a queue.

## Scale the app
Right now, your app is running on a single web dyno. Think of a dyno as a lightweight container that runs the command specified in the Procfile.

You can check how many dynos are running using the ps command:

![](heroku2.png)

By default, your app is deployed on a free dyno. Free dynos will sleep after a half hour of inactivity (if they don’t receive any traffic). This causes a delay of a few seconds for the first request upon waking. Subsequent requests will perform normally. Free dynos also consume from a monthly, account-level quota of free dyno hours - as long as the quota is not exhausted, all free apps can continue to run.

To avoid dyno sleeping, you can upgrade to a hobby or professional dyno type as described in the Dyno Types article. For example, if you migrate your app to a professional dyno, you can easily scale it by running a command telling Heroku to execute a specific number of dynos, each running your web process type.

Scaling an application on Heroku is equivalent to changing the number of dynos that are running. Scale the number of web dynos to zero:
```
      $ heroku ps:scale web=0
```      
Scale it up again:
```
      $ heroku ps:scale web=1
```
## Declare app dependencies
Heroku recognizes an app as Node.js by the existence of a package.json file in the root directory. For your own apps, you can create one by running npm init --yes.

The demo app you deployed already has a package.json, and it looks something like this:
     
![](heroku3.png)     

Run this command in your local directory to install the dependencies, preparing your system for running the app locally:
```
      npm install
      added 132 packages in 3.368s
```
## Run the app locally
Now start your application locally using the heroku local command, which was installed as part of the Heroku CLI:
```
     $ heroku local web
      [OKAY] Loaded ENV .env File as KEY=VALUE Format
      1:23:15 PM web.1 |  Node app is running on port 5000
```      
## Push local changes
In this step you’ll learn how to propagate a local change to the application through to Heroku. As an example, you’ll modify the application to add an additional dependency and the code to use it.

Begin by adding a dependency for cool-ascii-faces in package.json. Run the following command to do this:
```
      npm install cool-ascii-faces
      + cool-ascii-faces@1.3.4
      added 9 packages in 2.027s      
```
Modify index.js so that it requires this module at the start. Also add a new route (/cool) that uses it. Your final code should look like this:

![](heroku4)

Now test locally:
```
    $ npm install
    $ heroku local
```
Now deploy. Almost every deploy to Heroku follows this same pattern. First, add the modified files to the local git repository:
**git add .**

Now commit the changes to the repository:
**git commit -m "Add cool face API"**

Now deploy, just as you did previously:
**git push heroku main**

Finally, check that everything is working:
**heroku open cool**

## Provision add-ons
Add-ons are third-party cloud services that provide out-of-the-box additional services for your application, from persistence through logging to monitoring and more.

By default, Heroku stores 1500 lines of logs from your application. However, it makes the full log stream available as a service - and several add-on providers have written logging services that provide things such as log persistence, search, and email and SMS alerts.

Provision the papertrail logging add-on:
```
      heroku addons:create papertrail
      Adding papertrail on sharp-rain-871... done, v4 (free)
      Welcome to Papertrail. Questions and ideas are welcome (support@papertrailapp.com). Happy logging!
      Use `heroku addons:docs papertrail` to view documentation.
```
The add-on is now deployed and configured for your application. You can list add-ons for your app like so:
```  
    heroku addons
```
 Visit the papertrail console to see the log messages:
```
    heroku addons:open papertrail
```    
Your browser will open up a Papertrail web console, showing the latest log events. The interface lets you search and set up alerts:

![](heroku5.png)

## Start a console
To get a real feel for how dynos work, you can create another one-off dyno and run the bash command, which opens up a shell on that dyno. You can then execute commands there. Each dyno has its own ephemeral filespace, populated with your app and its dependencies - once the command completes (in this case, bash), the dyno is removed.

![](heroku6.png)

## Define config vars

At runtime, config vars are exposed as environment variables to the application. For example, modify index.js so that it introduces a new route, /times, that repeats an action depending on the value of the TIMES environment variable. Under the existing get() call, add another:
```
      .get('/times', (req, res) => res.send(showTimes()))
```
At the end of the file, add the following definition for the new function, showTimes():

![](heroku7.png)

To set the config var on Heroku, execute the following:
```
    heroku config:set TIMES=2
```
View the config vars that are set using heroku config:
```
    heroku config
    == sharp-rain-871 Config Vars
    PAPERTRAIL_API_TOKEN: erdKhPeeeehIcdfY7ne
    TIMES: 2
```
