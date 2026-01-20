**1. Creating a users and Group:**

**Use the base image of ubuntu and create a custom dockerfile that will have the user "Bob" and group "Developer" created.**

**Dockerfile:**

FROM ubuntu<br>
WORKDIR /app<br>
RUN groupadd Developer && useradd Bob<br>
RUN usermod -aG Developer Bob<br>
USER Bob<br>

RUN and verify commands:

docker run -it <container_id> bash<br>
whoami<br>
pwd<br>
groups<br>


**2.	Python Script Runner:-**

**Use a python image and run a Python script inside a container.**

**Dockerfile:**

FROM python:3.11.14-alpine3.23<br>
WORKDIR /app<br>
ADD https://raw.githubusercontent.com/ruchi13041995/Docker-projects/refs/heads/main/Python.py /app<br>
ENTRYPOINT ["python"]<br>
CMD ["Python.py"]<br>


**3.	Configurable Welcome Message:-**

 **Let the container print a message that can be changed by passing the environment variable.**

 **Dockerfile:**

FROM  ubuntu:22.04<br>
ENV WELCOME_MSG="Hello from Ruchi, welcome to DEVOPS!"<br>
# **Print the welcome message using shell (so variable expansion works)**<br>
CMD ["sh", "-c", "echo \"$WELCOME_MSG \""]<br>

RUN and verify command:

docker run <container_id><br>
docker run -e WELCOME_MSG="Lets start DEVOPS" <container_id><br>



