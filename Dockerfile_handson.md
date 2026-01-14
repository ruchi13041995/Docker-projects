**Scenario 1:**

**Create a Docker container that runs addition.py by default. When arguments are passed at runtime, the container should execute subtraction.py instead**
1.	Use the official Python base image
2.	Set the working directory to /apps
3.	Copy the Python scripts from Link-1(https://raw.githubusercontent.com/ruchi13041995/Docker-projects/refs/heads/main/addition.py) and Link-2(https://raw.githubusercontent.com/ruchi13041995/Docker-projects/refs/heads/main/Python.py) into the container
4.	Use ENTRYPOINT and CMD together to achieve the required behavior


**Dockerfile:**

FROM python:3.10.19-slim-trixie<br>
WORKDIR /apps<br>
ADD https://raw.githubusercontent.com/ruchi13041995/Docker-projects/refs/heads/main/addition.py /apps/<br>
ADD https://raw.githubusercontent.com/ruchi13041995/Docker-projects/refs/heads/main/Python.py /apps/<br>
ENTRYPOINT ["python"]<br>
CMD ["addition.py"]<br>



**Scenario 2:**
**Running Flask application.**
1. Create a Dockerfile that will run this(https://raw.githubusercontent.com/ruchi13041995/Docker-projects/refs/heads/main/menu_api.py) python program.
2.	Use base image as python:3.10-slim
3.	Copy the code into the container
4.	This code requires the flask package
5.	Code runs on port number 5000 bydefault.
6.	Create the Entrypoint or CMD to execute the code with command "python menu_api.py
7.	Create an image with "docker build . -t dinner-app" command.
8.	Run the image and map the port as well as per your wish.
9.	Confirm if code is running by opening up the http://localhost:<PORT>/menu on the browser OR you can run curl http://localhost:<PORT>/menu as well on your machine.


**Dockerfile creation:**

FROM python:3.10-slim<br>
WORKDIR /app<br>
ADD https://raw.githubusercontent.com/ruchi13041995/Docker-projects/refs/heads/main/menu_api.py /apps/<br>
RUN pip install --no-cache-dir flask<br>
EXPOSE 5000<br>
ENTRYPOINT ["python"]<br>
CMD ["menu_api.py"]<br>

**Building an image:**
docker build -t dinner-app .

**Run an image and bind to the port:**
docker run -p 5001:5000 dinner-app

**Verify using:**
curl localhost:5001/menu command
Also verify on browser using:
localhost:5001/menu command


**Scenario 3:**
**Upload above two images to your docker hub.**

**Uploading 1st image:**
docker login
docker tag addsub:latest ruchi134/addsub:v1.0
docker push ruchi134/addsub:v1.0

**Uploading 2nd image:**
docker tag dinner-app:latest ruchi134/dinner-app:v1.0
docker push ruchi134/dinner-app:v1.0







