---
layout: post
title: Getting Started on Heroku with Express and PostgreSQL
date: '2017-06-22 18:45:25 -0400'
categories: code snippets
---

# Introduction

This tutorial will have you deploying an Express app in minutes.

The tutorial assumes that you have:

- a free Heroku account
- node.js installed
- express installed

## Let's get started!

**RUN**

```
  express --view=ejs --css --git file_name

  cd file_name && npm install

  npm install nodemon --save

  npm install dotenv --save

  npm install cors --save

  npm install pg-promise --save
```
**THEN**

  open package.json & add:


	 "dev": "nodemon ./bin/www"



 **DO NOT FORGET THE COMMA PLEASE**

**NOW**

npm run dev will start your server on localhost:3000

**SO**

 create a .env file in the root directory

 **open .env & add:**

 	 DATABASE_URL= postgres://localhost:5432/db_name

**NOW**

 **in app.js enter:**

 	 require('dotenv').config();
 	 var cors = require('cors');
 	 app.use(cors());

**NOW**

In the root directory

**RUN**

```
mkdir db && cd db && touch queries.js

mkdir models && cd models && touch schema.sql && touch seed.sql
```

**open queries.js & add:**

	var pgp = require('pg-promise')();
	var connString = process.env.DATABASE_URL;
	var db = pgp(connString);

**THEN**

**RUN**

```
cd views && mkdir partials

cd partials

touch head.ejs

touch scripts.ejs
```

**NOW**

Create a .gitignore file and put your .env && node_modules directories inside

### Deploying the application and database to Heroku

```
 cd file_name

 git init

 git add .

 git commit -m "commit message"

 heroku create

 git push heroku master

```

**NOW YOU NEED TO...**




 Configure PostgreSQL addon for your application

 **SO**

 Download the postgreSQL addon on Heroku for your application

 **AND**

 Go to Resources/Administration/Credentials and enter the Heroku CLI into Terminal.

 ```
 ^Q out of that Database
 ```

 **Great!**

 **NOW**

 ```
 heroku pg:push db_name DATABASE_URL --app name
 ```


 **If for some reason a database has already been established (Who knows why, right??) RUN:**

```
heroku pg:reset
```

**THEN AGAIN PLEASE**

```
heroku pg:push db_name DATABASE_URL --app name
```

### Done!




### A few more things...


[Go here](https://www.npmjs.com) if you aren't familiar with any of the npm packages we just installed.

This should get you started but remember, this is just a reference sheet!

Work-flow should move like so: Database-->Server-Side--> Client-Side

Good luck building your application!

<div class="margin-space-article"></div>
