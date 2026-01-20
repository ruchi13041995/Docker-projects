**1. Install ping on top of Ubuntu:- Create a dockerfile that will have the "ping" package installed on top of Ubuntu:**

**ANSWER:**

**Dockerfile:**
FROM ubuntu
WORKDIR /app
RUN apt-get update && apt-get install -y iputils-ping

Commands outside container to verify :

docker build -t my_ping .
docker images
docker run <image_id/name>
ping google.com


**2. Print a Message:- Create a dockerfile that will print the "Hello - How are you" message when you run the image.**

**ANSWER**:

**Dockerfile**:

FROM ubuntu
CMD  echo "Hello - How are you"

Commands to build  and run:

docker build -t message .
docker run message:latest

**3.	Serve a Static HTML Page:-  Use httpd image to serve a customized message "Hello - This is a HTTPD Docker Container!". [Index.html path: /usr/local/apache2/htdocs/]**

**ANSWER:**

**Dockerfile:**
FROM httpd:2.4
COPY ./index.html /usr/local/apache2/htdocs/
WORKDIR  /usr/local/apache2/htdocs/
RUN  echo "Hello - This is a HTTPD Docker Container!">>index.html
EXPOSE 80

Run commands:

docker run -d -p 81:80 my_httpd:latest
curl localhost:81


