
<br>

# Flask(-Apache2-wsgi-Python3-Ubuntu) Docker container

<br>

This project was created to be able to have Docker container that accommodates Flask app (here, ***example Flask app***) which relies on apache2/wsgi/py3.

***Example Flask app***:

- is named BasicFlaskApp here;

- its role is only to verify that all works;

- it is a minimal Flask app;

- as there is not much content, it can be easily replaced with some other Flask app.

<br>

#### LONG DESCRIPTION

In other words, this project is for creating Docker image from which you could have Docker container consisting of:

- Apache (running web server)

- wsgi support configured on Apache

- python3 and pip3 set up

- Flask app (set up with wsgi and Apache; and running)

<br>

**You could use this project:** 

- **As a base for your own Docker image / Flask app that require similar characteristics (i.e., when starting new project from beginning).**

- **As a learning material, when learning Docker.**

<br>

## Running

### Test run

1. Clone the project.

2. `cd docker-flask-app-base-apache2-wsgi-py3`

3. Open docker-setup.sh and replace all occurrences of 'writeyourdockeridhere' with your docker id. Then run `sh docker-setup.sh`.

4. Verify that web app works. In browser, open: http://localhost:8888/. The webpage (of ***example Flask app***) should appear.

5. Cleaning up. Open docker-cleanup.sh and replace all occurrences of 'writeyourdockeridhere' with your docker id. Then run `sh docker-cleanup.sh`. 

<br>

### When using this project as a basis upon to build your own Flask web app


1. Clone the project.

2. Create a folder for your new project.

3. `cd <your project>`

4. Copy contents of cloned project to your project folder. Rename all occurrences of words 'BasicFlaskApp', 'basicflaskapp', 'bafla' with names that relate to/reflect your project. Introduce your code/edits. <br> Update requirements.txt, if needed (you might require different set of Python packages in your app; example on how to update: `pip3 freeze > requirements.txt`).

5. Once ready, do the test run (create Docker image, create isolated env (network), run Docker container, verify that web app works):

   5.1. `docker build -t <yourdockerid>/<yourimagename>:<yourimageversion> .`

   5.2. `docker network create <yourisolatednetworkname>`

   5.3. `docker run -d --name <nameyourcontainer> --net <yourisolatednetworkname> -p 8888:80 <yourdockerid>/<yourimagename>:<yourimageversion>`

   5.4. In browser, open: http://localhost:8888/. The webpage (of your Flask web app) should appear.
   
   5.5. Cleaning up. Stop and remove the container created in step 5.3. Remove the network created in step 5.2. 

<br>

## Notes

- Produced Docker image uses Ubuntu 18.04 as a base image.

- **Corresponding Docker images can be found at Docker Hub (hub.docker.com), under repository:** `dm4rnde/flask-app-base-apache2-wsgi-py3-ubuntu`
