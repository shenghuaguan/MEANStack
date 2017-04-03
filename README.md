# MEANStack

This is a course project from Udemy [Angular 2 (or 4) & NodeJS - The Practical MEAN Stack Guide](https://www.udemy.com/angular-2-and-nodejs-the-practical-guide/)

## Introduction

**Front End**
* Angular 2: run in brower (JavaScript) run on a single page, updates DOM, handles routing to load things faster

**Back End**
* NodeJS: server side code (JavaScript)
* ExpressJS: a framework wraps NodeJS (JavaScript)
* MongoDB

## Project Setup

1. Install NodeJS to run server-side code
2. Seed Project: includes ExpressJS and a basic project structure to get started quickly
3. Dependencies

Download NodeJS from `https://nodejs.org/en/` with lastest version v7.8.0current
Download seed zip folder and extract it, go into seed project then run `npm install`

```
# run client
npm run build

# run server
npm start
```

IDE: Webstorm


## MongoDB

Launch MongoDB Server to allow database operation
Launch MongoDB Client to interact with database

https://www.mongodb.com/download-center?jmp=nav#community
Community Server, default version is fine
Quick Start Guide: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/

```
sudo mkdir -p /data/db
sudo chown -R `id -u` /data/db

cd mongodb/bin

### server side
./mongod

### shell client: connect the mongodb server through terminal
./mongo

### database
use node-angular
show collections
db.messages.find()
```

 ## mongoose

 a replacement of **mongo node client** which require user write all the queries and access logic from mongo webpage
 a package more than mongo client which also allow use to define:
 * schemas & models
 * validation
 * intuitive database operations

install mongoose package
```
npm install --save mongoose
npm install --save mongoose-unique-validator
```

```javascript
router.get('/', function (req, res, next) {
    // findOne get the first row in the database
    User.findOne({}, function(err, doc) {
        if (err) {
            return res.send('Error!');
        }
        res.render('node', {email: doc.email});
    });
});
```

## Angular 2

**Single page application** only use single page

`polyfills.ts` import the polyfills we need, so our application can run on multiple browsers
`main.ts` import polyfills.ts, is the first file to run when executing bundle.js in index.hbs file

`decorator` is attached to class

* Property Binding: pass a value from parent to child
* Event Binding: pass a value from child to parent through event
* Directives:
    * are instructions Angular 2 will execute
    * Components are directives (with a view, the template)
    * use selectors to let Angular 2 know which parts of the HTML code represent instructions
    * Kind: attribute/structural directives

Attribute directive:

```
<article class="panel panel-default" [ngStyle]="{backgroundColor: color}" (mouseenter)="color='green'">
```

Structural directive: start with `*`

```
<div class="container">
    <div class="row">
        <div class="col-md-8 col-md-offset-2">
            <app-message
                    [message]="message"
                    (editClicked)="message.content = $event"
                    *ngFor="let message of messages"></app-message>
        </div>
    </div>
</div>
```

