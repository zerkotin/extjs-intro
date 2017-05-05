# The Stores
Stores are used for data storage, it can be stored on the Client or Server side

## A simple store
The store is a very complex Object, lets break it down to the necesities
1. Local Store
2. Remote Store

The best reference for stores since its a complex Object is the [Sencha Documentation](http://docs.sencha.com/extjs/6.2.1/classic/Ext.data.Store.html)  


### Local Store

Example
```javascript
var store =  Ext.create('Ext.data.Store', { //a store without a model
             data : [
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

store.getAt(0); //get record number 0

TODO add examples for add update and delete
```

To be continued...




