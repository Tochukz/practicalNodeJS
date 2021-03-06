# Practical NodeJS
[Source Code](https://github.com/azat-co/practicalnode/tree/master/code)
## Chapter 1: Setting up Node.js and Other Essentials  
#### Run node debugger  
After placing the `debug` statement on different lines on the script, run the command:  
`$ node inspect hello-debug.js`  
**Use the following command while in the debugger interative shell:**  
`cont`, `next`, `step`, `out`, `watch` or `c`, `n`, `s`, `o`.  
#### Install node inspector globally  
`$ npm install -g node-inspector@0.7.5`  
#### Running the node-inspector  
`$ node --inspect-brk hello-debug.js`  
For older version of Node you may do  
`$  node --inspect --debug-brk hello-debug.js`
#### Installing mongoDB driver  
`$ npm install mongodb --save`  

## Chappter 2: Using Express to Create Node.js App  
#### Installing Express.JS
This will install express locally to the project.  
`$ npm init -y`  
`$ npm install express@4.15.4 --save --exact`  

#### Creating an express app   
**Here we use the express CLI to create an express app with it's skeleton/scaffolding**  
* Install the Express.js Generator. This will give us the express CLI   
`$ sudo npm install -g express-generator@4.15.5`  
* Confirm that express has been installed correctly  
`$ express --version`  
* You can take a look at the CLI options  
`$ express --help`  
* Create an express project  
`$ express --css sass express-app`  
* Install dependencies:  
`$ cd express-app && npm install`  
* Run the app:  
`$ DEBUG=express-app:* npm start`  
* Open up your browser and enter `http://localhost:3000/` in the address bar.  

#### Creating express app manually  
Here we create an express app manually without using the express generator.  
* Create the package.json config file  
`$ npm init`  
* Install express  
`$ npm install express@4.15.4 --save`  
* Install pug  
`$ npm install pug@2.0.0-rc.4 --save`   
* Install stylus  
`$ npm install stylus@0.54.5 --save`  
* Assuming you have choosen app.js as your entry point you can start you server using any of the following commnd  
`$ node app.js`   
`$ node app`  
`$ node start`  
* If you choose index.js as your entry point, you can start you server using  
`$ node `  

## Chapter 3: TDD and BDD for Node.js with Mocha
#### Install Mocha
Installing mocha gloablly  
`$ sudo npm install -g mocha`    
Installing a specific version of mocha to a specific project:    
`$ npm install mocha@4.0.1 --save-dev`
To run tests using the globally installed mocha test runner:
`$ mocha tests`  
This will run all tests in the 'tests'  directory.  
To run tests using the locally installed mocha, in the root directory of the project, do:    
`$ node_modules/.bin/mocha tests`  

#### Installing the Chai Assertion Library
`$ npm install chai@4.1.2 --save-dev`  

#### Installing the stand alone Expect.JS Library
`$ npm install expect.js --save-exact`  

#### Run the test using make.
Define the target entry and commands in a 'makefile', after that do:  
`$ make `  
See [Using Make and writing Makefiles](https://www.cs.swarthmore.edu/~newhall/unixhelp/howto_makefiles.html)  
Check if the make file is properly tabbed by doing:  
`$ cat -e -t -v makefile`  
This will show all the tabs as ^I and all the line ending as $. Each command in the make file must start with a tab and end with end line.  
Use regular text editor to write your makefile.  

## Chapter 4: Template Engines: Pug and Handlebars
#### For the pug-example demo:
Create package.json file  
`$ npm init -y `  
Install express  
`$ npm install express --save`  
Install pug  
`$ npm install pug --save`  
Installing nodemon  
`$ npm install --global nodemon`

__Express application with handlebars enabled__
Installation of express with handlebars enabled  
`$ express --view hbs handlebars-examples`   



__Stand alone handlebars__
Installation of handlebars for standalone  
`$ npm install handlebars --save`    

Handlebar.js or `handlebars` is an extension to the Mustache templating language.   
Handlebars is largely compatible with Mustache templates.  
`hbs` is Express.js view engine for handlebars.js.  

For precompilation, install handlebars globally  
`$ npm install -g handlebars`  

[Read Handlebar Article](https://www.sitepoint.com/a-beginners-guide-to-handlebars/)  
[Handlebars CND](https://cdnjs.com/libraries/handlebars.js/)  

## Chapter 5: Persistence with MongoDB and Mongoskin
**Installation of mongodb-clients**    
`$ sudo apt install mongodb-clients`  
**This should install both mongoDB server and client**  
`$ sudo apt install -y mongodb`  
**Check mongoDB version**  
`$ mongod --version`  
**Start the mongoDB server**  
`$ sudo service mongodb start`  
**Check the status, stop and restart  mongoDB server**  
`$ sudo service mongodb status`  
`$ sudo service mongodb stop`  
`$ sudo service mongodb restart`  
**Starting the mongoDB client**  
`$ mongo`  
**Installing nodeJS native driver for mongoDB**  
`$ npm install mongodb@2.2.33 -SE`  
**Installing mongoskin mongoDB driver for nodeJS**  
`$ npm i mongoskin@2.1.0 -SE`  
`mongoskin` 2.x requires `mongodb` 2.x to be installed before it can work properly.
#### Basic MongoDB operations using the mongo console.  
**First start the mongodb service**  
`$ sudo service mongodb start`  
**Next, start the MongoDB client**  
`$ mongo`
##### Operations
**Show all exiting databases**  
`$ show databases`  or  
`$ show dbs`  
**Select a database to work with**  
`$ use blog`  
**Create a collection**   
`db.createCollection("users")`  
**Show all collections in the selected database (Collections in NoSQL DBs is  synonymous  to tables in RDBMS)**  
`$ show collections`  
**Add documnets to a collection named 'people'.This will create the collection automatically of it does not exist.**
```
$ db.people.insert({name: 'Chichi', city: 'Lagos'});
$ db.people.insert({name: 'Chukwudi', city: 'Kaduna'});  
$ db.people.insertOne({name: 'Clayton', city: 'Cape Town'})
$ db.people.insertMany([{name: 'Chichi', city: 'Lagos'}, {name: 'Chima', city: 'Aba'}])
```
**You may also use the save method**  
`$ db.people.save({name: 'Chucks', city: 'Cape Town'});`  
MondoDB will create the 'people' collection if it does not exists  

**Find the total number of documents in the collection**  
`$ db.people.count()`  

**Query the people collection  (Will display all documents  where city == 'Lagos'. It is case sensitive)**  
`$ db.people.find({city: 'Lagos'})`  
**To get  a single document instead of a set of documents**  
`$ db.people.findOne({city: 'Lagos'})`  
 **Show all documents in the 'people' collection**  
 `$ db.people.find()`  
**Delete document(s) matching a query parameter (Deletes all documents where city == 'Lagos')**   
`$ db.people.remove({city: 'Lagos'})`
**Update a document in a collection**  
```
$ db.people.find()                               // Show all the current documents in the collection
$ var chichi = db.people.findOne(name: 'Chichi)  // Assign the document to be updated to a variable  
$ printjson(chichi)                              // Visualize the document object
$ chichi.city = 'Texas';                         // Update the document object property
$ printjson(chichi)                              // Verify the update
$ db.people.save(chichi)                         // Save the updated document to the collection  
$ db.people.find()                               // See the updated document in the collection
```
The save() method acts like an upsert(update or insert)- If you  have MongoDB `_id`, then the document will be updated with the new properties passed to save() else it will insert a new document and create a new document ID.  

#### Writing a simple bash script to seed the database with data from a json file using the mongoimport module.    
1. Create the sh file db/seed.sh
2. Write the following in the first line of the script file  
`#!/bin/bash`   
3. Write your commands one line after another
```
mongoimport --db blog --collection users --file ./users.json --jsonArray
mongoimport --db blog --collection articles --file ./articles.json --jsonArray
```
4.  After saving the script with .sh extention, make it executable  
`$ chmod u+x seed.sh`
5. Run the script
`$ ./db/seed.sh`  
The mongoimport module can work with json, CSV OR TSV

Usefull links  
[MongoDB interactive shell](https://docs.mongodb.com/manual/mongo/)

## Chapter 6: Security and Auth in Node.js  
#### JSON Web Token (JWT) Authentication  
Developers use JSON Web Tokens(JWT) to encrypt data which is then stored on the client.  
JWTs have all the information unlike regular tokens(API keys or OAuth access tokens), which are more like passwords.  JWT is less secure then web sessions because encryption can be broken given enough time and processing power.
The JWT has three parts: header, payload and signature. The encryption method may vary: HS256, RS512, ES384 and so on.
The stronger the algorithm, the better. RS512 will be good for most of the cases circa 2020.  

__Implementing JSON Web Token (JWT) authentication__  
Installing jsonwebtoken package  
`$ yarn add jsonwebtoken`  
Installing bcrypt package  
`$ npm install --save bcrypt`    

__Implementing session Authentication__  
We need two modules to implement session authentication - `cookie-parser` and `express-session`  
From version 1.5.0 of  `express-session`, it is recommended to use `express-session` by itself without `cookie-parser`.  

Install cookie-parser and express-session     
`$ npm i cookie-parser express-session -SE`   

NB: The `cookie-parser` and `express-sesion` module is recommended  over the use of `cookie-session`. This is because `cookie-session` stores all information in the cookie, not the server. `express-session` uses secure in-memory or Redis storage - and cookies store only for the session ID.

### OAuth Module
Find the OAuth module `oauth` on [npm]  (https://www.npmjs.org/package/oauth) and [Github](https://github.com/ciaranj/node-oauth)   
It is recommended that `node-auth` be used when complex integration is needed or when only certain pieces of OAuth are needed.  

Installing OAuth  
`$ npm install auth@0.9.15`  

## Chapter 9: Real-Time Apps with WebSocket, Socket.IO, and DerbyJS  
[About HTML5 WebSocket](http://www.websocket.org/aboutwebsocket.html).  
Installing the websocket module  
`$ npm install ws@3.3.0 -SE`  
Learn more about the `ws` at [npm](https://www.npmjs.com/package/ws) and  [github](https://github.com/websockets/ws)

Setup an express scaffolded application  
`$ express socket-app --view=pub`  
`cd socket-app && npm install`  


Websocket connections can use the standard ports: 80 for a HTTP and 443 for HTTPS  

### Redis
[Redis Quick Start](http://redis.io/topics/quickstart)   
[How to Install Redis on Windows 10](https://www.youtube.com/watch?v=188Fy-oCw4w)  

__Using the source files to install redis__   
* Go to [github.com/microsoftarchive/redis/releases](https://github.com/microsoftarchive/redis/releases)   
* Navigate to the latest releases  
* Download the `zip` file  
* Create a "redis" directory in your system's `c` drive  
* Unzip the downloaded file inside the created "redis" directory  
* Copy the location path of the `redis-server` file  
* Add the path as environment variable to your system  
* Open up a command interface and start the server `$ redis-server`  
* Open up another command interface and start the client `$ redis-cli`  
* On the `redis-cli` prompt enter the command: `ping`, and should get a `PONG` response  

__Using the MSI installer to install redis__  
* Go to [github.com/microsoftarchive/redis/releases/](https://github.com/microsoftarchive/redis/releases)  
* Navigate to the latest releases  
* Download the `msi` installer and following the wizard  
* Make sure to check the '_add to path_' checkbox when you see it  
* After successful installation the server will be started automatically    
* open a command interface and do `$ redis-cli`  
* On the `redis-cli` prompt enter the command: `ping`, and your should get a `PONG` response     

Redis runs  on 127.0.0.1:6379 by default.  

__Basic Redis CLI operations__  
Lunch the redis-cli to access the CLI prompt    
`$ redis-cli`

Setting a key-value pair  
`redis 127.0.0.6379> set name Chucks`  

Reading a value of a key    
`redis 127.0.0.6379> get name`

### Online collaborative code editor  
Installing all the require dependencies  
`$ npm install derby express livedb-mongo racer-browserchannel redis`  


## Chapter 11:
__Keeping Node.js Apps Alive__
There are a couple of options to choose from.  
* [forever](https://github.com/foreversd/forever)
* [Upstart](http://upstart.ubuntu.com/)
* [init.d](https://www.unix.com/man-page/opensolaris/4/init.d)  

__Forever__  
Installing Forever globally:      
`$ npm install forever -g`     
Start a Node Server with Forever:       
`$ forever start server.js`    
Start Node Server with options for log files:      
`$ forever start -l forever.log -o output.log -e error.log server.js`  
Step Node Server process:      
`$ forever stop server.js`    
List all Node Servers running on Forever:    
` forever list`  
Look up available commands:  
`$ forever --help`   

__Warning__ The app won’t start on server reboots without extra setup/utilities.
