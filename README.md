## Project Description

This is a simple HTTP server writen in python.
This projects the use of jenkins as a continuous integration pipeline.
The `Jenkinsfile` contains declarative script that outlines the steps of the continuous integration.

There are four stages of the pipeline as per the Jenkinsfile.

- The first stage is the **SonarQube Analysis** stage which performs static testing of the aplication code and ensures it passes any set Quality Gates.
- The sceond stage is the **Build** stage which uses the Docker engine to build a container image from the application code.
- The third stage is the **Containerize and Test** stage which runs the application in a conatiner to ensure that it works. 
