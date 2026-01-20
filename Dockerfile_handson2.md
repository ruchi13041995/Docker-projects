**1. Install ping on top of Ubuntu:- Create a dockerfile that will have the "ping" package installed on top of Ubuntu:**

**ANSWER:**

**Dockerfile:**

FROM ubuntu<br>
WORKDIR /app<br>
RUN apt-get update && apt-get install -y iputils-ping<br>

Commands outside container to verify :

docker build -t my_ping .<br>
docker images<br>
docker run <image_id/name><br>
ping google.com<br>


**2. Print a Message:- Create a dockerfile that will print the "Hello - How are you" message when you run the image.**

**ANSWER**:

**Dockerfile**:

FROM ubuntu<br>
CMD  echo "Hello - How are you"<br>

Commands to build  and run:

docker build -t message .<br>
docker run message:latest<br>

**3.	Serve a Static HTML Page:-  Use httpd image to serve a customized message "Hello - This is a HTTPD Docker Container!". [Index.html path: /usr/local/apache2/htdocs/]**

**ANSWER:**

**Dockerfile:**

FROM httpd:2.4<br>
COPY ./index.html /usr/local/apache2/htdocs/<br>
WORKDIR  /usr/local/apache2/htdocs/<br>
RUN  echo "Hello - This is a HTTPD Docker Container!">>index.html<br>
EXPOSE 80<br>

Run commands:

docker run -d -p 81:80 my_httpd:latest
curl localhost:81


