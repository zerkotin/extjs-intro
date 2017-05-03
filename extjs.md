# ExtJS on 1 leg

In this section we will learn the basics of ExtJS, the Class system, Layouts, Components and Stores through short and useful examples.


## Hello World
Lets compare the Sencha way with the *Raw* way

### The Raw way of hello world
In another world a *Hello World* application would take some minimal effort, it would require us to create a minimum of:
- .HTML, 
- .CSS
- .JS
- Running a Web server

You need to install a Web server, choose build tools, configure them, install pluging, bundler, CSS preprocessors.
or alternatively use some boilerplate/Yeoman.  
__Pros__: you get flexibility and a huge community support (provided that you choose carefully).  
__Cons__: its work and you have to maintain it.

### The Sencha way of hello world
Now what will consist of creating a *Hello World* application in ExtJS, lets see...
- Running a *Generate Command* (you can take a peak into the [CMD page](cmd.md))
- Running `sencha app watch`

You have a running webserver and an application with a whole skeleton.  
Not to mention you also have all the following:
- Build tools setup
- Repository
- Sass
- Production build
- bundler, minifier and uglifier
- Watcher
- Web server
- Ready to use complex UI components
- Cross browser compilation
- Responsiveness out of the box
- Documentation
- Themes
- Touch support

__Pros__: saves lots of time.  
__Cons__: not flexible, uncostumizable and support is from Sencha provided you bought ExtJS license or found your answers on the internet.

But, enough with CMD, lets see some code examples...

### Hello world
```
Ext.Viewport.add({
    xtype: 'panel',
    html: 'Hello World!'
});
```
What do we see here? a _Viewport_, and what is that _xtype_ ?  




