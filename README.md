Flashify
========

Flash notifications for Express 3 applications

Installation
============

Firstly install the module via npm:

    npm install flashify
    

Then require it into your application:

    var flashify = require('flashify');

Then tell Express to use the middleware in your configuration function:

    app.use(express.cookieParser('secret'));
    app.use(express.session());
    app.use(flashify);

Usage
=====

Flashify binds itself to your request object so you can easily
set a flash notification by the following:

    app.get('/secret', function(req,res){
      req.flash('Sorry, go away');
      req.redirect('/');
    });

Inside your view, you can loop through and get the flash by the following 
(Example in Jade):

    if (flash.message != undefined)
      li= flash.message

Custom Types and Multiples
==========================

You can queue up multiple flash messages with custom types using the same methods as above:

    app.get('/secret', function(req,res){
      req.flash('error', 'Some silly error');
      req.flash('error', 'Some other silly error');
      req.flash('this still queues up as well!')
      req.flash('error', 'Some other other silly error');
      res.redirect('/');
    });