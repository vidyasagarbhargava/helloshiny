# These steps are for Shiny applications.
In your Shiny application source's root directory:
* Create a Dockerfile file and insert the following content. FROM virtualstaticvoid/heroku-docker-r:shiny
* ENV PORT=8080
* CMD ["/usr/bin/R", "--no-save", "--gui-none", "-f", "/app/run.R"]
*    
* Create a heroku.yml file and insert the following content. build:
*   docker:
*     web: Dockerfile 
* Commit the changes, using git as per usual. git add Dockerfile heroku.yml
* git commit -m "Using heroku-docker-r FTW" 
* Create the Heroku application with the container stack heroku create --stack=container  Or configure an existing application to use the container stack. heroku stack:set container 
* Deploy your application to Heroku, replacing <branch> with your branch. E.g. master. git push heroku <branch> 
* Scale the web dyno heroku scale web=1 
