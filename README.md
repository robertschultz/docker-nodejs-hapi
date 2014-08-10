Introduction
----

Docker configuration for a node.js related stack with hapi. This will allow you to create a node.js image to spin up a bare bones node.js stack using hapi middleware.

Build Docker Image
---
    docker build -t <yourname>/docker-nodejs-hapi .

This will build a local Docker image that uses the base node image and configures npm and your working directory in the container.

Run New Node Container
---
    docker run -d -P <yourname>/docker-nodejs-hapi

This will initialize a new container and run your node application as a background daemon.

Container Port
---
    docker ps

Docker will create and assign a random port to route calls from your host machine to your new node.js instance. You should see your new container here with a port mapping like below.

    CONTAINER ID        IMAGE                                    COMMAND             CREATED             STATUS              PORTS                     NAMES
    f2e505d0f3d9        robertschultz/docker-nodejs-hapi:latest            bin/www             11 hours ago        Up 51 minutes       0.0.0.0:49153->3000/tcp   high_blackwell

Test
---
    curl http://<ip>:49153

You should see a typical HTML response back from your node.js server depending on how you configured it.

    <!DOCTYPE html><html><head><title>Express</title><link rel="stylesheet" href="/stylesheets/style.css"></head><body><h1>Express</h1><p>Welcome to Express</p></body></html>
