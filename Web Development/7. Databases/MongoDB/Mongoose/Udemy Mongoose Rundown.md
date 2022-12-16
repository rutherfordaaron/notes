# What is Mongoose?

Mongoose is an Object-Document Mapping Library (ODM). It is a JS library that helps us focus on logic rather than queries when using MongoDB, much like how Sequelize helps us abstract MySQL. We define models and queries are handle behind the scenes.

The core concepts are that we create shemas and models to define our data, use instances to create data, the create queries with that data.

[Mongoose Docs](https://mongoosejs.com/docs/)

# Connecting to the Database Server

To start using Mongoose, we first need to install it via npm with `npm i mongoose`. Next, we import Mongoose and setup a connection.

```JS
const mongoose = require('mongoose');
...
mongoose.connect(databaseURI)
  .then(result => app.listen(3000))
  .catch(err => handleError(err));
```

Note that the `.connect()` method returns a promise. And from here we are connected to our database!