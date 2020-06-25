## Docusaurus v1 and v2 containerised

I wanted to try out a static document generation program, and this was a good fit.

Quick and easy Dockerfile and build for node, based on the node:lts-alpine image.

I saw a whole bunch of options for containers, but this was a chance to build some skeleton node Dockerfiles for other projects too.

[Docusaurus Github] (https://github.com/facebook/docusaurus)
[Node.js] (https://hub.docker.com/_/node)

## Run v1

Run the test server node provides and iterate:

`docker run --name docusaurus -p 3000:3000 -v /my/existing/docusarus/project:/home/node/docusarus cpasternack/docusarus-build:latest`

Run the production image to build the site: 

`docker run --name docusaurus -p 3000:3000 -v /my/existing/docusarus/project:/home/node/docusarus cpasternack/docusarus-build:production`

## Run v2 alpha

Image defaults use "website" and "classic" templates. Build your own with `ARG WEBSITE_NAME=<my_cool_pages>` and template `ARG TEMPLATE=<my_new_template>`

`docker run --name docusaurus-v2 -e SITE=<name_of_website_folder> -p 3000:3000 -v /my/existing/docusarus/:/home/node/docusarus/$SITE cpasternack/docusarus-build:v2-latest`

`docker run --name docusaurus-v2 -e SITE=<name_of_website_folder> -p 3000:3000 -v /my/existing/docusarus/:/home/node/docusarus/$SITE cpasternack/docusarus-build:v2-production`

## Volumes:

Mount your own v1 docs: `-v /path/to/your/md/docs:/home/node/docusaurus/docs`
Mount your own v1 website: `-v /path/to/your/md/docs:/home/node/docusaurus/website`

or just:

`-v /path/to/your/site:/home/node/docusaurus`


Mount your own v2: `-e SITE=mysite -v /path/to/your/project:/home/node/docusaurus/mysite`


## If something doesn't work:

Sorry. I am trying my best and learning. The original projects' documentation and githubs are pretty active, that's where I put this together from.

## Updates:

I will be updating this as and when I can. I only put this up publically because I had a hard time finding a container that was up-to-date, and I didn't want to do a full node install to get the dockerfile to build from v1.

I'll try and bump this to node 14.4.x+ on alpine3.12+ when I get a chance.

Please fork from github as needed.

## License:

MIT
