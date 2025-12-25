---
---
**General Heroku notes**

if you need to search buildpacks, run **heroku buildpacks:search \[whatever application you're needing\]**

when starting a build, Heroku will try starting it three times

unless you **login via the CLI**, neither the heroku command nor the git commands will work right

Buildpacks

if you add a buildpack via the command line, you will automatically see them added in the Heroku **Settings** page

\***YOU DO NOT NEED A PROCFILE WHEN PUSHING YOUR REACT APP TO HEROKU AND HAVE IT WORK\***

If you run a cli command and it doesn't seem to recognize the app you need the **\-a APPNAME** behind a command
