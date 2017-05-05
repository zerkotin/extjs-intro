# The Stores
Stores are used for data storage, it can be stored on the Client or Server side

## A simple store
The store is a very complex Object, lets break it down to the necesities
1. Local Store
2. Remote Store

The best reference for stores since its a complex Object is the [Sencha Documentation](http://docs.sencha.com/extjs/6.2.1/classic/Ext.data.Store.html)  


### Local Store
A local store will remain in memory and is not referencing anything from the server.  

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



