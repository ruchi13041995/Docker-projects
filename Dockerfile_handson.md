Scenario 1:

Create a Docker container that runs addition.py by default. When arguments are passed at runtime, the container should execute subtraction.py instead
1.	Use the official Python base image
2.	Set the working directory to /apps
3.	Copy the Python scripts from Link-1 and Link-2 into the container
4.	Use ENTRYPOINT and CMD together to achieve the required behavior


Dockerfile:

FROM python:3.10.19-slim-trixie
WORKDIR /apps
ADD https://raw.githubusercontent.com/TechTitans-Academy/Experiments-hub/refs/heads/main/Dockerfiles/addition.py /apps/
ADD https://raw.githubusercontent.com/TechTitans-Academy/Experiments-hub/refs/heads/main/Dockerfiles/subtraction.py /apps/
ENTRYPOINT ["python"]
CMD ["addition.py"]




