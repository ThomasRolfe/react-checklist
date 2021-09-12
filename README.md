# File changes

Inside the public/index.html file add the following to the manifest import

> crossorigin="use-credentials"

-   Ensure Helmet or similar is used to update site titles and meta. If not, change the public/index.html file title and placeholder CRA data

-   Update manifest.json data in public folder

-   Generate favicons

-   Generate site logo for manifest to use

-   Update meta theme color

-   Remove app.css if not in use

-   Include an env.example file with blank credentials if in use

-   Create a 404 page and route handler

## Git

-   Make sure gitignore is ignoring the .env file if in use

-   Make sure gitignore is ignoring build folders. Perform build step on server unless server is incapable of doing so. In which case, perform build step on master branch, merge to prod and push to server

# Deployment

Hosting on plesk, requires node to be active.

Use the server.js template file in the root directory and point node to this file to serve the app. [Server Repo](https://github.com/ThomasRolfe/react-server)

Set Application root to /httpdocs

Set Document root to /httpdocs/build

Setup git webhook for the plesk subscription & add the following additional actions for auto build:

> PATH=/opt/plesk/node/12/bin:$PATH; npm install && npm run build &> npm.log

> touch tmp/restart.txt

\*Assuming the paths remain the same for the node installation. Adjust path and node version if necessary.

In Plesk > web hosting access > system user, set the following the ensure node can run builds and installs successfully.

> Access to server over ssh - /bin/bash

Add .npmrc file to httpdocs folder for NPM compatibility [NPMRC file](https://github.com/ThomasRolfe/npm-fix)
