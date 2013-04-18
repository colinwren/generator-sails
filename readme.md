# Sails yeoman generator prototype


This a prototype of sails yeoman integration, this repo is mostly copied from
[generator-webapp](https://github.com/yeoman/generator-webapp), I don't think this is the best solution for Yeoman sails integration but this repo is for expirimenting with and discussing the integration.  The best solution would be for yeoman to have a a configurable backend and so you would just be able to specify the server you wanted to use like:
```
yo webapp --sails
yo angular --sails
yo chromeapp --express
```

## Installation
```
npm install -g generator-sails
```
Make sure you have ```yo``` installed, if not run
```
npm install -g yo
```
## Creating a Sails Yeoman project
* Make a folder for your project

```
mkdir testProject && cd testProject
```

* Run the generator command

```
yo sails
```
* Answer the questions and wait for the huge amount of node pacakges to download
* Start the sails server and grunt watch process using grunt

```
grunt server
```
This will start the sails server and the grunt watch processes, you will need to reload the page because the ```open``` task fires before the server starts. The sails server will restart when files change and the grunt watch process will auto-compile your assets.

Add ```console.log 'yay sails'``` to ```app/scripts/hello.coffee``` and reload your browser (I haven't gotten livereload to work without a browser extension on dynamic pages) and it will have logged ```yay sails```

While your grunt server process is running, in another terminal run ```sails generate cat``` and navigate to 
[http://localhost:1337/cat/create](http://localhost:1337/cat/create), (you might need to reload the page once the server restart is slow). The server will have restarted with the new models and controllers and return you the JSON for a new cat.


# Todo
1. Currently you can't run sails with yeomans production build because you can't change the folder that static files are served from or the server environment without changing config files
2. The assets folder doesn't do anything, it is there because sails uses it for asset rack and will throw errors if you remove it
3. Get livereload working, this means having the sails starter page be static which makes sense for buidling ajax apps
4. Because such minor changes had to be made to the Yeoman generator to get this working, it would be easy to get sails to work with any Yeoman generator.  It should be an option for Yeoman to use a sails backend instead of the connect middleware static server

