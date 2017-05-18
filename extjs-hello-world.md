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
__Cons__: it's work and you have to maintain it.

### The Sencha way of hello world
Now what will creating a _Hello World_ application in ExtJS consist of? lets see...  
- Running a *Generate Command* (you can take a peak into the [CMD page](cmd.md))
- Running `sencha app watch`

You have a running webserver and an application with a whole skeleton.  
Not to mention you also have all of the following:
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
__Cons__: not flexible, uncostumizable and support is from Sencha provided you bought an ExtJS license or found your answers on the internet.

But, enough with CMD, lets see some code examples...

### Hello world
```
Ext.create('Ext.panel.Panel',{
  html: 'Hello World!',
  renderTo: Ext.getBody()
});
```
What do we see here? a _Panel_, and what is that _Ext.create_ ?  
We will get there, lets start with [Ext Classes](extjs-classes.md) first.



