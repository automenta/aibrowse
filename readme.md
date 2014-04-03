# Collaborative Virtual Browser

Uses PhantomJS with Node, Angular and Socket.io to create a Virtual Browser which may be used by multiple devices collaboratively.

This is an extract from Pongells's Master Thesis at ETHZ (GlobIS): **An infrastructure for cross-device mashups**


# AI Web Browser that Can Learn and Follow High-Level Commands (Coming Soon)

Since all browser interaction can be recorded, sequences of events can be associated with the page context, and the user's goal.

* Watch: record interaction events (and paths to the associated elements) and associate them with features of the current page (such as the domain name, page structure, etc...), and an optionally human-specified Goal label.
* Do: a menu of known Goals (consisting of browser events applied to page elements) which may apply to the current page

This represents an embodiment environment for cognitive agents to intelligently browse the web.


## Installation

Install PhantomJS and add the runnable to the PATH env. variable (i.e. typing `phantomjs` in a terminal should start PhantomJS).

```
npm install ; cd public ; bower install ; cd ..
```


## How does it work?

Pages are open inside a virtual browser (PhantomJS) which simply put is like a real browser, but running on the server (no need for a GUI).

Once open, the page DOM is extracted, modified and sent to the interested clients. Since we are using Socket.io for communication, users interested in a page join the Socket Room called `pageId`.

Events on the client (click, change, submit) are sent to the server, which replays them inside the virtual browser and then sends the result back.

You can see it as a remote desktop kind of application, but with js and html pages.


##Note
Disable logging if it gets slow by setting the 'verbose' flag in app.js.  Otherwise it will print a lot of output. Each time a page changes or it finishes loading resources, the whole page is sent to the registered clients.

A batter way to do this would be to use MutationObserver (or some other trick) and only send updates instead of the whole document.


## Tools
Server:
* Node.js
* Express
* Jade
* Socket.io
* phantomjs-node
* Cheerio

Client:
* AngularJS
* Socket.io
* angular-socket-io
* Bootstrap 3.0
* jQuery
