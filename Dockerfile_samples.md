Docker File Samples:

🧱 1. Simple Python App:
Use Case: Run a Python script.

# Use official Python base image
FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Copy dependencies and install them
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy source code
COPY . .

# Run the application
CMD ["python", "app.py"]
🌐 2. Node.js Web Server
Use Case: Run a Node.js web app.

FROM node:20

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000
CMD ["node", "server.js"]
🧪 3. Alpine-based Bash Script Runner
Use Case: Lightweight image to run shell scripts.

FROM alpine:3.19

RUN apk add --no-cache bash

COPY ./script.sh /app/script.sh
RUN chmod +x /app/script.sh

CMD ["/app/script.sh"]
🛠️ 4. Ubuntu web server with apache2
Use Case: Ubuntu image with apache server running.

# Getting the Operating System.
FROM ubuntu

# Installing the HTTP package.
RUN apt update && apt install apache2 -y

# Create index.html file.
RUN echo "Hello From Docker Container" > /var/www/html/index.html

# Starting the HTTP service.
CMD ["apachectl", "-D", "FOREGROUND"]
