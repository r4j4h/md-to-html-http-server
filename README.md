md-to-html-http-server
======================

A miniature markdown to html HTTP converter in node.js. With Dockerfile &amp; Makefile to build as an image and run a container on a given point.

**Note: Not tested. Not ready. In development**

.plan
--------
- Simple server
  - Looks for 'md' parameter in request
  - Passes to markdown.
    - var markdown = require( "markdown" ).markdown;
    - return markdown.toHTML(str);
  - Returns the html to response
- Create Dockerfile
  - Build Steps (docker build -t md2htmlsvr .)
    - Phusion ubuntu or tianen/centos:6.5
    - Install node & npm
    - Add files
    - Execute npm install
    - Set ENTRYPOINT to run server
    - Ready
  - Run Steps
    - Start a container that is removed upon exit from the built image, forwarding the port the server listens on to whatever the user desires on their machine (via Makefile or args)
      - docker run --rm md2htmlsvr 8000
        - Example that would run the server, forwarding port 8000 to the node web server inside the container.
- Create Makefile
  - Wrap build command
  - Wrap run command
  - Default target should build and then run

