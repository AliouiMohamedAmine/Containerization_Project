# Containerization Project: VProfile Application

## Overview
This project demonstrates the containerization of the **VProfile Application** using **Docker** and **Docker Compose**. The application stack includes multiple services such as a **MySQL database**, **Memcached**, **RabbitMQ**, a **Tomcat application server**, and an **Nginx web server**. Each service is containerized and orchestrated using Docker Compose for easy deployment and management.

---

## Key Features
- **Containerization**: Each component of the VProfile application is containerized using Docker.
- **Orchestration**: Docker Compose is used to manage and run the multi-container setup.
- **Portability**: The entire application stack can be deployed on any system with Docker installed.
- **Scalability**: Individual services can be scaled independently as needed.

---

## Project Structure
vprofile-containerization/
├── Docker-files/
│ ├── db/ # Dockerfile for MySQL database
│ ├── app/ # Dockerfile for Tomcat application
│ └── web/ # Dockerfile for Nginx web server
├── compose.yml # Docker Compose configuration file
├── README.md # Project documentation


## Services Overview
The following services are defined in the `compose.yml` file:

1. **vprodb**:
   - **Description**: MySQL database for the VProfile application.
   - **Image**: Custom-built image (`aliouimohamedamine/vprofiledb`).
   - **Port**: `3306` (MySQL).
   - **Volume**: Persistent storage for MySQL data (`vprodbdata`).

2. **vprocache01**:
   - **Description**: Memcached service for caching.
   - **Image**: Official `memcached` image.
   - **Port**: `11211` (Memcached).

3. **vpromq01**:
   - **Description**: RabbitMQ service for message queuing.
   - **Image**: Official `rabbitmq` image.
   - **Port**: `5672` (RabbitMQ).
   - **Environment**: Default credentials (`guest:guest`).

4. **vproapp**:
   - **Description**: Tomcat application server for the VProfile application.
   - **Image**: Custom-built image (`aliouimohamedamine/vprofileapp`).
   - **Port**: `8080` (Tomcat).
   - **Volume**: Persistent storage for application data (`vproappdata`).

5. **vproweb**:
   - **Description**: Nginx web server for serving the application.
   - **Image**: Custom-built image (`aliouimohamedamine/vprofileweb`).
   - **Port**: `80` (HTTP).
