##Hosting a webserver - project 5

###What is it?

Daniel McVicker's solution for Udacity Full-Stack Nanodegree project 5.

This is a book catalog that demonstrates basic CRUD (create, read, update, delete) functionality, along with some basic 
image handling, JSON and XML API endpoints, Oauth2 providers, csv parsing and some other concepts deployed to Amazon's AWS service.

###Information

* You can take a look at the server at 52.88.93.141 on port 2200. 
* You can use the application at http://52.88.93.141/

####Some notable software that was installed and config changes made:
* Apache + mod_wsgi
* PSQL
* Setup and configured grader user
* updating installed packages using apt-get
* changed firewall configuration to secure
* installed fail2ban (very useful when restarting the box)
* verified that local timezone was set to UTC
* git
* Flask
* pip
* glances + pysensors
* use "history" command for full list of me stumbling around. 

###Resources used: 
https://github.com/stueken/FSND-P5_Linux-Server-Configuration and the resources linked to in that walkthrough were mostly enough. Some stray google searches for specific issues were also used to refresh my memory.

Something I figured out along the way: https://discussions.udacity.com/t/boolean-gotchas-in-psql-vs-sqlite/46737

###Installation


To take a look at the project, run

    python setup.py

from the directory you are currently in.
Setup can take a long time as the database has to be instantiated and nearly 1000 entries 
must be imported. You can use the catalog by navigating to http://localhost:8000

Note that if your environment differs from the vagrant environment that this project is contained in, you will likely need to
run files in this sequence to install:

    python database_setup.py
    python importer.py

Again, setup can take a long time.

**To simplify setup, you may wish to install vagrant.** 

For a brief overview of installing vagrant, check here:

https://www.udacity.com/wiki/ud197/install-vagrant

Once you've installed vagrant, start a session with the vagrant machine by navigating to the \vagrant\tournament directory
(in git bash for Windows or your terminal program for Mac) and type the following commands:

    vagrant up

Once the machine comes up, start an ssh session by typing

    vagrant ssh

Once that is complete, navigate to the \fullstack\vagrant\catalog\ directory.

###Usage

Start the server by typing 
    
    python catalog.py 
    
You can use the catalog by navigating to http://localhost:8000
You can stop the catalog by pressing ctrl + c.

####API Endpoints:

You can get data in JSON or XML formats:

#####To return JSON/XML for a specific category with category_id.

    http:localhost:8000/category/<int:category_id>/books/JSON
    http:localhost:8000/category/<int:category_id>/books/XML

#####To return JSON/XML serialized information for a specific book in category_id with book_id.

    http:localhost:8000/category/<int:category_id>/books/<int:book_id>/JSON
    http:localhost:8000/category/<int:category_id>/books/<int:book_id>/XML

#####To return JSON/XML serialized information for all categories.

    http:localhost:8000/category/JSON
    http:localhost:8000/category/XML

###Sources

I have heavily used the classwork from Udacity, documentation from Flask, Jinja and the [unicodecsv module](https://pypi.python.org/pypi/unicodecsv/0.14.1). I based the bookshelf css code on this [demo]
(http://www.bootply.com/jme11/7h2JKXv40U)

Thanks for taking a look. 
