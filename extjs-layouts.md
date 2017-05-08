# ExtJS Layout System
The layouts will help you decide the Components's placement and flow throughout the page.

## Lets meet some basic layouts
- Absolute Layout
- Accordion Layout
- Border Layout
- Card Layout
- Card (Tabs)
- Center Layout
- Column Layout
- Fit Layout
- HBox Layout
- Table Layout
- VBox Layout
- Auto Layout

### Lets concentrate, because these are too many layouts, what do we really need?
1. Fit Layout - it will basically fill the entire parent container
2. Border Layout - a layout which has South, North, West, East and Center positions
3. HBox - Horizontal Box, The flow of the item will be horizontal
4. VBox - Vertical Box, the flow of the items will be vertical 

In most cases, these will do, if you want to see them in action,  
you can take a look at the [Layouts Kitchen Sink](http://examples.sencha.com/extjs/6.2.1/examples/kitchensink/#layouts) from Sencha.

## How do we use layouts?

Components are placed in _Containers_ and _Containers_ are using layouts to determine the child components's placement.


### The container

A simple panel is a container, in most cases we will use either a _Panel_ or it's Ancestor _Container_.  


Here's an example of a _Panel_ using a _Column_ layout and contains 2 items (which are components)
```javascript
Ext.create('Ext.panel.Panel', {
    renderTo: Ext.getBody(),
    width: 400,
    height: 200,
    title: 'Container Panel',
    layout: 'column',
    items: [
        {
            xtype: 'panel',
            title: 'Child Panel 1',
            height: 100,
            columnWidth: 0.5
        },
        {
            xtype: 'panel',
            title: 'Child Panel 2',
            height: 100,
            columnWidth: 0.5
        }
    ]
});
```

What can we make of it?
1. the _Panel_ class has a _layout_ config
2. the _Panel_ class has a _items_ config
3. there's that _xtype_ again, what is that?!

### xtype and requires
Altough it has nothing to do specifically with _Layouts_ it does requires a short explanation.

Consider the next example
```javascript
//person class
Ext.define('My.sample.Person', {
  alias: 'person' //mind the alias config
}); 

//some container
Ext.create('Ext.panel.Panel', {
    renderTo: Ext.getBody(),
    requires: [ //mind the requires config
      'My.sample.Person'
    ],
    items: [
        {
            xtype: 'person' //we have a person component
        },
        {
            xtype: 'person' //and another person component
        }
    ]
});

```

Conclusion
1. when not using `Ext.create` and the full component name, we can use the _alias_ config to provide a shortcut name
2. we still need to _require_ every external file, thus the _requires_ config, this is in order for the bundler to import the file when building the application

#Important
__Always__ provide a _layout_, the auto layout does not comply with resizing and scrollbars.

What now? [Stores](extjs-stores.md)!
