# The Stores
Stores are used for data storage, it can be stored on the Client or Server side

## A simple store
The store is a very complex Object, lets break it down to the necessities  
1. Local Store
2. Remote Store

Since its a complex Object the best reference for the store is the [Sencha Documentation](http://docs.sencha.com/extjs/6.2.1/classic/Ext.data.Store.html)  


### Local Store

Example
```javascript
var store =  Ext.create('Ext.data.Store', { //a store without a model
     data: [
         {firstName: 'Peter',   lastName: 'Venkman'},
         {firstName: 'Egon',    lastName: 'Spengler'},
         {firstName: 'Ray',     lastName: 'Stantz'},
         {firstName: 'Winston', lastName: 'Zeddemore'}
     ]
});
```

### Remote Store

Example
```javascript
store = Ext.create('Ext.data.Store', { //ajax store
     proxy: {
         type: 'ajax',
         url: 'users.json'
     },
     autoLoad: true //this is not a must, but it saves time
});
```

### Useful Store API

CRUD 
```javascript
store.load({ //ajax: HTTP GET; local store: load the 'data' attribute
    callback: function(){
        console.log(arguments);
    }
}); 

store.load({ //sending an ajax call with params: localhost/users.json?userid=22216&foo=bar
    params : {
        userid : 22216,
        foo    : 'bar'
    }
});
        
store.reload(); //send the las call

store.loadData([]); //loads an array of records into the store silently

var record = store.getAt(0); //get record number 0

store.add({firstName: 'lori', lastName: 'gingis'}); //adds data to the end of the store, accepts: Ext.data.Model[] / Ext.data.Model... / Object[] / Object...
store.insert(0,[]); //loads an array of records with a specified index (not at the end like 'add')

store.remove(record); //removes a record/records
store.removeAt(0); //removes a record at a specific index, params: index, count
store.removeAll(); //removes all records, params: silent
```

Note that there is no 'update', to update a record, you can simply update the reference to a _Model_ using it's setters
Example
```javascript
var record = store.getAt(0);
record.set('lastName', 'Yo'); //this is an update
```

## A Model
A Model, is a representation of a persistent Object

### The simple Model

```javascript
Ext.define('User', { //defining a model template
    extend: 'Ext.data.Model', //the model extends the base sencha model
    fields: [ // a set of fields and their types
        {name: 'name',  type: 'string'},
        {name: 'age',   type: 'int',
        {name: 'phone', type: 'string'},
        {name: 'alive', type: 'boolean'}
    ]
});

var user = Ext.create('User', { //creating an instance of the model
    id   : 'ABCD12345',
    name : 'Conan',
    age  : 24,
    phone: '555-555-5555'
});

user.get('name'); //an automatic getter - returns Conan
user.set('name', 'Conan Jr.'); //an automatic setter for updates
```

### Remote Model
All Models can have _Proxies_ same as stores

Example
```javascript
Ext.define('User', {
    extend: 'Ext.data.Model',
    fields: ['id', 'name', 'email'],

    proxy: {
        type: 'rest',
        url : '/users'
    }
});

var user = Ext.create('User', {name: 'Ed Spencer', email: 'ed@sencha.com'});

user.save(); //POST /users

User.load(123); //GET users/123

user.set('name', 'Edward Spencer');
user.save(); //update

user.erase(); //delete
```

### The Model Store
Stores can also say what type of data they are expecting, if a proxy is defined in the Model, it will use that proxy

Example
```javascript
var store = new Ext.data.Store ({ //preferably use Ext.create
    model: 'MyApp.model.User'
});
```

Now that we know all the basics, lets take a look at a full MVC example of a grid with a controller, a view model a  model and a store [MVC](extjs-mvc.md)
