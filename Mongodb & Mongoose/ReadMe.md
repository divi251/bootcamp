![enter image description here](https://actyv-bootcamp.s3.ap-south-1.amazonaws.com/banners/mongodb.jpg)
# MongoDB and Mongoose
MongoDb is  No-SQL based Database. In this type of dataBase data is save like an object of JS. 
So we dont have to save the data in form of rows and columns. This is why it is known as a schemas-less database. 

Example : If we are creating a database having some information of students then database where it save, will look like : 

     {
        "name": "Divyansh",
    
         "age": "24",
         "subject": ["mathematics", "science", "Hindi"] 
        }
        
    {
         "name": "Himanshu",
          "age": "20",
          "subject": ["mathematics", "science", "litrature"] 
          }


But in SQL it will be shown as tables which have row of names which contains name and row of age which will contain the age. But here it is saving in form of documents or JSON document or object which looks like same

## Comparision and representation
If we see in SQL Database, data is stored as tables which contain rows but in mongodb it is called collection which keeps Document or you can say  JS Object as data.
In mongo DB table will be the collection and row will be a document or JS object. Each JS object will contain keys/field and values, that key/field is like the column.
See the following image and compare it.


![enter image description here](https://cdn-media-1.freecodecamp.org/images/oxeGaPqbZ2pmmZx3WcDo8CXIL4J09PbecBWW)


So Database in mongodb will contain a Database and that database contains the collections and collection will contain the data. As we can see in following figure that one collection (Table) is containing many fields (Row) and values (Colum). Fields are same in each documents but values (column) are changing (See the figure of collections).

![enter image description here](https://cdn.educba.com/academy/wp-content/uploads/2019/04/MongoDB-chart2.jpg)


![enter image description here](https://docs.mongodb.com/manual/_images/crud-annotated-collection.bakedsvg.svg)


**Now let just compare the queries :**
The following figure will shoq the comparisons for CRUD operations in MongoDB and RDBMS like SQL. Because everything will be handled as file or object , so to acces that we put dot operator as we do in js to acces the keys of objects

**Comparing Codes :** 
![enter image description here](https://www.simform.com/wp-content/uploads/2017/11/table2.png)



## BASIC  KEYS   IN MongoDb

**SCHEMA:**
A schema is an object that defines the structure of any entry you will store in the database. For example, if you want to store a book detail in the db then you need to define the properties of the book like book's name, id and author. That defining of properties of an entry is called a Schema. 

In RDBM or SQL they are having schemas or structure like rows and columns in a proper alignment But MongoDB is Schema-Less.We use Mongoose to create schemas.

 **MODEL** : Model is an object that gives you easy access to a named collection, allowing you to query the collection and use the Schema to validate any documents you save to that collection.
    
  **DOCUMENT** : Each entry in a collection is a Document.
    
 **COLLECTION** : All the documents are stored in a collection which in our case is "books" collection.
 
 **SHARDING** : Sharding is the process of storing data records across multiple machines and it is MongoDB's approach to meeting the demands of data growth.

**REPLICATION** : Replication is the process of synchronizing data across multiple servers. Replication provides redundancy and increases data availability with multiple copies of data on different database servers.

## Let Just Start Coding
(Prerequisites : JS, basic 'Express' Folder structure Understanding)

Open the code folder in mongoDB repository and  see the folder structure here:

```
.
├── app.js
├── bin
│   └── www
├── package.json
├── connection
│   ├── mongoose.js
├── .gitignore

```

First thing whenever you clone a node.js repo is run  `npm install`  in your terminal to install all the node_modules defined in package.json.

First navigate to  `connection/mongoose.js`. Here you can see on top we are requiring  `mongoose`  like  `const mongoose = require("mongoose")`  . Mongoose provides a straight-forward, schema-based solution to model your application data. In simple words, Mongoose acts as an intermediate between mongodb and server side language (like NodeJs).

Then next you must be seeing the below line:

`require("dotenv").config();`

We will talk about this in detail. But for now just look at what is does. So  `dotenv`  is an npm package which loads the environment variables from the  `.env`  file into the application and make them accessible through  `process.env.KEY_NAME`. Now coming to next part, how to actually make a connection to MongoDB.

```
mongoose.connect(process.env.mongoURI, {
    useNewUrlParser:  true,
    useUnifiedTopology:  true
});

```

Mongoose provides a connect method which takes two parameters as follows: 1. Mongo URI : Connection Url which you got from Atlas before. 2. options: Some MongoDB parameters.

You can read more about what parameters it supports from here:  [https://mongoosejs.com/docs/connections.html](https://mongoosejs.com/docs/connections.html)

Now let's go through the Event Handlers which are as follows:

1.  `connected`  - This piece of code will run when the connection is established successfully. So if you want to perform some tasks after a connection is established you can do them here.

```
mongoose.connection.on("connected", () => {
    console.info("MongoDB connected Successfully!!");
});

```

2.  `error`  - This piece of code will run when the mongoose driver will not be able to make a connection to mondoDB.

```
mongoose.connection.on("error", err  => {
    console.error(`Error in mongoose connection: ${err.message}`);
});

```

3.  `disconnected`: This piece of code will run whenever the driver is disconnected from the Atlas server.

```
mongoose.connection.on("disconnected", () => {
console.info("Mongoose connection is disconnected");
});

```

4.  `SIGINT`: This piece of code will run whenever there is an unexpected shutdown of the server or somehow unexpectedly the driver is disconnected.

```
process.on("SIGINT", function() {
    mongoose.connection.close(() => {
        process.exit(0);
    });
});

```

Now we haven't create a  `.env`  file yet. So if you run only this it will show error like cannot find variable  `mongoURI`  or it is undefined. So let's create it first. Add a file and name it as  `.env`  in the root folder and insert below line:

`mongoURI: <your connection url from Altas>`

Remember we used to register our routes in  `app.js`. Same thing we have to do here also. We need to require this file once in app.js. So if you open app.js you will find the following line

`require("./connection/mongoose");`

This is just like running a script. When we require it means we are running the javascript present in that file. So if we require like this, it will run and establish a mongDB connection. Remember there was this line  `console.info("MongoDB connected Successfully!!");`  in the  `connected`  event handler in  `connection/mongoose.js`  file. This will print "MongoDB connected Successfully!!" in your console if the connection is established successfully otherwise if not it will print error to your console.

Note: console.log() is a very bad practice. In future we will learn how to use and configure a logger.

Now if you run this using  `npm start`  it will require the mongoose connection and connection will be established. Next step is to insert data to it but before that we need to learn some terminologies which will be helpful throughout the bootcamp.



**Schema, Model, Document and Collection:**

Now move to branch  `database/schema`  like we did before.

Now you will see a new folder named  `schema`. Open  `schema/index.js`.

Like we did before we first import  `mongoose`  on top, then in next line we are extracting  `Schema`  method from mongoose.

```
const Schema = mongoose.Schema;

```

Then we defined a user schema as follows:

```
const userSchema = new Schema({
    <property_name>: <property_type>
})

```

Example:

```
const userSchema = new Schema({
    firstName: String
})

```

This can also be written as follows:

```
const userSchema = new Schema({
    firstName: {
        type: String
    }
})

```

The benefit of the above method is we can define other properties as well, like in below example

```
const userSchema = new Schema({
    firstName: {
        type: String,
        minlength: 6
    }
})

```

`minlength`  will add a validation that minimum length of the firstName should be 6 otherwise the document will not be inserted in the collection. You can read more about schema types here:  [https://mongoosejs.com/docs/schematypes.html](https://mongoosejs.com/docs/schematypes.html)

Now see the last line in schema/index.js :

`module.exports = User = mongoose.model("User", userSchema);`

Here we are exporting a mongoose model.  `mongoose.model`  will take two parameters:

1.  Collection name which in this case is "User"
2.  Schema

So now each entry/document of user will be the part of "user" collection in Atlas.

**Instance, Static Methods and Virtuals:**

1.  Instance Methods: These are the methods which are used to manipulate the individual document like  `updateUserByName(`),  `findUserById()`. Some of them are already provided by a mongoose driver as explained here:  [https://mongoosejs.com/docs/queries.html](https://mongoosejs.com/docs/queries.html). We also can create our custom instance methods which we are going to learn in a bit.
    
2.  Static Methods: These are the methods which are used to query the whole collection. We will do an example of the same in a bit.
    
3.  Virtuals: Virtuals are the document properties that you can get and set but that do not get persisted to MongoDB like for example there are two properties in your schema one is firstName and other is lastName. Now there is a requirement there in which you have to print the full name. One way is to do like this  `firstName + " " + lastName`, another is  `${firstName} ${lastName}`. But the best way would be if we can directly access like User.fullName. So what virtuals does is, it creates a virtual property  `fullName`  to the schema but this property will not be persisted in the database but we can access this like  `User.fullName`.
    

💡  ****Pro Tip :****  The Schema, Instance Methods and Virtuals are applied on a Schema not on a Model.

Let's see an example for each one of those:

Change your branch to  `database/schema-methods`

You will see a new folder  `methods`  in the root directory. Open  `methods/index.js`.

As I said above theses methods (static, instance and virtuals) are applied on the schema rather than the model first step will be to import that schema like below.

`const { userSchema } = require("../schema/index");`

Now you might be wondering why I used destructuring here but not in other imports. You will get your answer as you move further.

First let's see how to define  **instance methods**. Consider the following piece of code.

```
userSchema.methods.getIfAdult  =  function() {
    return  this.age >  18;
};

```

`this`  is a keyword that will give refer to the current user object.

Now you might also be wondering why I did not use arrow functions here like below:

```
userSchema.methods.getIfAdult  = () => {
    return  this.age >  18;
};

```

So there is this one thing about arrow functions that they have no scope means we cannot use  `this`  keyword here.

Now lets describe some  **static methods**. There are two ways in which you can define static methods.

Method 1:

```
userSchema.statics.findByAge  =  function(age, callback) {
    this.find({ age: age }, callback);
};

```

Method 2:

```
userSchema.static("findByLastName", function(lastname, callback) {
    this.find({ lastname: lastname }, callback);
});

```

Now let's see how can we implement  **Virtuals**.

```
userSchema.virtual("fullName").get(function() {
    return this.firstname + " " + this.lastname;
});

```

This will create a virtual property  `fullName`  and whenever we will call  `user.fullName`  it will return  `this.firstname + " " + this.lastname;`

We will run all these while implementing controllers in next topic.

**Important:**  For all these methods to work it is important to require them before creating the model out of schema. Otherwise, they will not be a part of mongoose objects.

So now if you remind we create and export the model in schema files. So open "schema/index.js" and move to last. You will see the below lines.

```
module.exports.userSchema = userSchema;              ---- Line 1
require("../methods/index");                         ---- Line 2
const User = mongoose.model("User", userSchema);     ---- Line 3
module.exports.User = User;                          ---- Line 4

```

Let's see them one by one. First focus on line 2. As I said before creating and exporting the model we have to require the above methods. So Line 2 does that.

But why there are two exports.  🤔

If you open  `methods/index.js`  you will see on top we have to import user schema. So before requiring methods in the schema we have to export the schema so that methods/index.js can consume the schema.

And now since we have to export two objects here one is model and other is the schema. Therefore there are 2 module.exports. So now we are exporting the following object  `{userSchema, User}`, and this is the reason we import like this  `const { userSchema } = require("../schema/index");`  in our methods file.

















