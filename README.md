# My Docker Notes - Project 2
Author: mlinx | Docker Hub: dockmee001

A lightweight notes app with custom 404, containerized with nginx:alpine (62.9MB).

### Demo
- Main: http://localhost:8080
- 404 Test: http://localhost:8080/hacker

### Docker Proof
REPOSITORY: notes-app
TAG: v1
IMAGE ID: b917b54905f2
SIZE: 62.9MB
Base: nginx:alpine

### Files in ~/notes-app/
- index.html - Notes app with timestamp (localStorage)
- 404.html - Custom "Lost in Docker Space?" page
- Dockerfile - FROM nginx:alpine
- nginx.conf - error_page 404 /404.html
- README.md - This file

### Dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/
COPY 404.html /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/conf.d/default.conf

### nginx.conf
server {
 listen 80;
 root /usr/share/nginx/html;
 index index.html;
 error_page 404 /404.html;
 location = /404.html {}
 location / { try_files $uri $uri/ =404; }
}

### Run Commands
sudo docker build -t notes-app:v1 .
sudo docker run -d -p 8080:80 --name my-notes notes-app:v1
sudo docker ps
sudo docker images | grep notes-app

### Features
- Save notes with timestamp
- Custom 404 working
- 62.9MB clean image
- No dangling <none> images

Made with Docker + Nginx
