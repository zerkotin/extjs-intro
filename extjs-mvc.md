# MVC / MVVC
Yes, some call it MVC, some MVVC, there are so many Theories out there and the borders are very blury.  
In general, we have a Seperation of Concern with Model/View/Controller.  
and this is how its done in ExtJS:  
- [Ext.data.Model](http://docs.sencha.com/extjs/6.2.1/classic/Ext.data.Model.html)
- [Ext.data.Store](http://docs.sencha.com/extjs/6.2.1/classic/Ext.data.Store.html)
- [Ext.app.ViewModel](http://docs.sencha.com/extjs/6.2.1/classic/Ext.app.ViewModel.html)
- [Ext.app.ViewController](http://docs.sencha.com/extjs/6.2.1/classic/Ext.app.ViewController.html)
- [Ext.panel.Panel](http://docs.sencha.com/extjs/6.2.1/classic/Ext.panel.Panel.html)

Lets see a real example using the [Grid](http://docs.sencha.com/extjs/6.2.1/classic/Ext.grid.Panel.html)  

```javascript
Ext.define('Myapp.viewmodel.UsersViewModel', {
    extend: 'Ext.app.ViewModel',
    alias: 'viewmodel.user',
    stores: {
        simpsonsStore: {
            storeId: 'simpsonsStore',
            fields: ['name', 'email', 'phone'],
            data: [
                {
                    name: 'Lisa',
                    email: 'lisa@simpsons.com',
                    phone: '555-111-1224'
                },
                {
                    name: 'Bart',
                    email: 'bart@simpsons.com',
                    phone: '555-222-1234'
                },
                {
                    name: 'Homer',
                    email: 'homer@simpsons.com',
                    phone: '555-222-1244'
                },
                {
                    name: 'Marge',
                    email: 'marge@simpsons.com',
                    phone: '555-222-1254'
                }
            ]
        }
    }
});

Ext.define('Myapp.viewcontroller.UsersController', {
    extend: 'Ext.app.ViewController',
    alias: 'controller.user',

    init: function () {
        console.log('controller is started!!! yay!!!');
    },

    onGridSelection: function() {
        console.log(arguments);
    }
});

Ext.create('Ext.panel.Panel', {
    viewModel: 'user',
    controller: 'user',

    items: [
        {
            xtype: 'grid',
            title: 'Simpsons',
            bind: {
                store: '{simpsonsStore}'
            },
            columns: [
                {
                    text: 'Name',
                    dataIndex: 'name'
                },
                {
                    text: 'Email',
                    dataIndex: 'email',
                    flex: 1
                },
                {
                    text: 'Phone',
                    dataIndex: 'phone'
                }
            ],
            listeners: {
                select: 'onGridSelection'
            },
        }

    ],
    height: 200,
    width: 400,
    renderTo: Ext.getBody()
});
```

You can see this example in action [here](https://fiddle.sencha.com/#view/editor&fiddle/1v7i)

Have fun coding!
