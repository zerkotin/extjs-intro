# ExtJS Class System
First of all, we need a place to practice, we can practice all at [Sencha Fiddle](fiddle.sencha.com)

## A simple class
Lets create a simple class in ExtJS syntax
```javascript
Ext.define('My.sample.Person', {
    name: 'Unknown',

    constructor: function(name) {
        if (name) {
            this.name = name;
        }
    },

    eat: function(foodType) {
        console.log(this.name + " is eating: " + foodType);
    }
});

var bob = Ext.create('My.sample.Person', 'Bob');

bob.eat('Salad'); // "Bob is eating: Salad"
```

Simple enough, we have the Class name, and an object containing the contents of the class.  
Note the _constructor_ and the use of _this_.  

## Basic class features
```javascript
Ext.define('My.own.Window', {
   extend: 'Ext.Component',

   config: {
       title: 'Title Here',

       bottomBar: {
           height: 50,
           resizable: false
       }
   },

   applyTitle: function(title) {
       if (!Ext.isString(title) || title.length === 0) {
           alert('Error: Title must be a valid non-empty string');
       }
       else {
           return title;
       }
   },

   applyBottomBar: function(bottomBar) {
       if (bottomBar) {
           if (!this.bottomBar) {
               return Ext.create('My.own.WindowBottomBar', bottomBar);
           }
           else {
               this.bottomBar.setConfig(bottomBar);
           }
       }
   }
});

/** A child component to complete the example. */
Ext.define('My.own.WindowBottomBar', {
   config: {
       height: undefined,
       resizable: true
   }
});
```

### What features do we see in that class?
1. `extend` - used for inheritance/extension
2. `config` - a block used to expose API just like in modules, it also provides a lifecycle which we will shortly discuss
3. `applyTitle` - `apply` and `update` are called as a part of the lifecycle of a config, in addition it also provides a getter and a setter
4. `My.own.WindowBottomBar` - a 2nd component which is used as a child component

### How do we use that?
```javascript
ar myWindow = Ext.create('My.own.Window', { //creating my own window
    title: 'Hello World',
    bottomBar: {
        height: 60
    }
});

alert(myWindow.getTitle()); // alerts "Hello World"

myWindow.setTitle('Something New'); //setting new title

alert(myWindow.getTitle()); // alerts "Something New"

myWindow.setTitle(null); // alerts "Error: Title must be a valid non-empty string"

myWindow.setBottomBar({ height: 100 });

alert(myWindow.getBottomBar().getHeight()); // alerts 100
```

### Statics
A short example that creates a factory using statics and config
```javascript
Ext.define('Computer', { //a computer class
    statics: {
        instanceCount: 0, //just for example
        factory: function(brand) { //creates a new Computer instance and passes the 'brand' config to the constructor
            // 'this' in static methods refer to the class itself
            return new this({brand: brand}); //we can just add the config in the constructor
        }
    },

    config: {
        brand: null //brand config, now we have a getter, a setter, apply and update
    }
});

var dellComputer = Computer.factory('Dell'); //create a dell computer
var appleComputer = Computer.factory('Mac'); //create a Mac

alert(appleComputer.getBrand()); // using the auto-generated getter to get the value of a config property. Alerts "Mac"
```

Now lets see some [Layouts](extjs-layouts.js)



