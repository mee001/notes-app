# Project 5: Multi-Service with MongoDB
Date: Sep 21

Services:
- notes-app: nginx on 8080:80 with website-data volume
- mongo: mongo:6 on 27017 with mongo-data volume

Persistence Verified:
- docker volume ls shows notes-app_mongo-data and notes-app_website-data
- docker ps shows 2 containers Up
- Compose file has depends_on and 2 volumes

Learning: Multi-service compose, volume for DB persistence
