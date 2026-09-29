Step  1: Created the GitHub project "jenkins-docker-cicf-lab" entirely in the browser

Opened a Codespaces in Github to create a flask app. 


Browser
   │
   ▼
GitHub Codespaces
   │
   ├── Python
   ├── Flask App
   └── Git
   │
   ▼
GitHub Repository


Step 2: Directly from your GitHub project using Codespaces

Created a Dockerfile inside app directory.  It will automatically installer docker 

Checking docker version in bash terminal:
----------------------------------------
$ docker --version
Docker version 29.8.0-1, build 88096ef00576baf72a9cb45caa45c0544c40e0a7

$ docker --version
Docker version 29.8.0-1, build 88096ef00576baf72a9cb45caa45c0544c40e0a7

Build the docker image
----------------------
$cd app
$docker build -t my-flask-app:v1  .

wait to complete. 
$ docker images
 IMAGE             ID             DISK USAGE   CONTENT SIZE   EXTRA
my-flask-app:v1   9b6f2c6b7cdf        198MB         48.3MB 

At this point:
-------------
GitHub Project
      ↓
Dockerfile
      ↓
docker build
      ↓
my-flask-app:v1

Run docker image
----------------
 $ docker run -d --name flask-app -p 5000:5000 my-flask-app:v1
11c7b0e57645b5a58434f2441d8b081e179f96f800bc0691d91f9b29ca8f9ced

$ docker ps 
CONTAINER ID   IMAGE             COMMAND           CREATED          STATUS          PORTS                                         NAMES
11c7b0e57645   my-flask-app:v1   "python app.py"   21 seconds ago   Up 21 seconds   0.0.0.0:5000->5000/tcp, [::]:5000->5000/tcp   flask-app

Test the application:
---------------------
$ curl http://localhost:5000/health
{"status":"healthy"}


we can also open in browser 

Save Dockerfile to GitHub:
--------------------------
$ git status 
$ git add .
$ git commit -m "Add Docker configuration"
$ git push
