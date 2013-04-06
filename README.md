Canned fake API server
======================
Working with APIs, more often than not, during development you want to work
with a fixed version of the responses provided. This is especially true if the
API is still under development, and maybe even still needs input on how to
output something. This is what Canned is for!

What does it do?
----------------
Canned maps a folder structure to API responses, so

    /comment/any.get.json

becomes

    HTTP GET
    Content-Type: application/json
    {
      content: 'I am a comment',
      author: 'sideshowcoder'
    }

Awesome! so what is supported?
------------------------------
Currently Canned supports the basic REST-API mapping, as well as custom method
mapping with nested endpoints.


    file                        | response
    /index.get.json             | GET /
    /any.get.json               | GET /:id
    /_search.get.json           | GET /search
    /comments/index.get.json    | GET /comments/
    /comments/any.get.json      | GET /comments/:id
    /comments/_search.get.json  | GET /comments/search

Ok I need this!
---------------
Just install via npm

    $ npm install canned

How do I use it
---------------
There are 2 ways here, either you embed it somewhere programmatically

    var canned = require('canned')
    ,   http = require('http')

    can = canned('/path/to/canned/response/folder')

    http.createServer(can).listen(3000)

Or just run the provided canned server script

    $ canned

Which serves the current folder with canned responses

License
-------
MIT 2013 Philipp Fehre alias @sideshowcoder


