# Sencha CMD

## Using the CMD

A simple sencha command will usually look like:  
`sencha [category] [command] [options]`

Example:  
`sencha app build development`  
This will compile the app at the current folder


The options are as follows:

```
Categories
  * app - Perform various application build processes
  * compile - Compile sources to produce concatenated output and metadata
  * cordova - Quick init Support for Cordova
  * diag - Perform diagnostic operations on Sencha Cmd
  * fs - Utility commands to work with files
  * generate - Generates models, controllers, etc. or an entire application
  * manager - Commands for interacting with Sencha Web Application Manager.
  * manifest - Extract class metadata
  * package - Manages local and remote packages
  * phonegap - Quick init support for PhoneGap
  * repository - Manage local repository and remote repository connections
  * template - Commands for working with templates
  * theme - Commands for low-level operations on themes
  * web - Manages a simple HTTP file server

Commands
  * ant - Invoke Ant with helpful properties back to Sencha Cmd
  * audit - Search from the current folder for Ext JS frameworks and report their license
  * build - Builds a project from a legacy JSB3 file.
  * config - Load a properties file or sets a configuration property
  * help - Displays help for commands
  * js - Executes arbitrary JavaScript file(s)
  * upgrade - Upgrades Sencha Cmd
  * which - Displays the path to the current version of Sencha Cmd
  ```
  
### Generating a new App

To generate a new App skeleton:  
`sencha -sdk /extjs-repository-path generate app AppName /app-name-path`

### Building the app

To compile sass and bundle the sources for production:  
`sencha app build`

To compile for development without the bundling part:  
`sencha app build development`

To compile for development with a watcher and a webserver:  
`sencha app watch`  
in this case, after compilation the app is available at `http://localhost:1841/`  

### Generating a package

Packages can be dynamically loaded and/or be reused in several projects.  

To generate a package:  
`sencha generate package package-name`  

### Building a package

To build a package:  
`sencha package build`  

## The Repository

### Listing

To list the contents of the local repository:  
`sencha repository list`  

### Add to repository

To add a package to the local repository:  
`sencha package add foo.pkg`  


