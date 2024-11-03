# DevOps Assigment 2 - GitHub Actions & DockerHub

## Description of Workflow

So, obviously the original code was already extensively commented, and I kinda just copy/pasted the file over here. I'm going to try to explain what the workflow is doing in my own words. There are 3 main jobs:

### Compile the WorkOrder Pro Springboot application to a Java JAR
This part of the yaml is the compilation process for the java project, obviously. The workflow first needs to actually install the JDK in order to compile it. This is because the operating system that the job is executed in is essentially a fresh build of Ubuntu. Once the JDK is installed, the job uses gradlew to build it into a JAR file. The code also renames the .jar to "app.jar" and creates an artifact for the job it just completed.

### Build the JAR application into a docker image


## Link to DockerHub Repository
[DockerHub - `YOURLASTNAME-WOPro-Service`](place link here)

## Link to GitHub Actions Run Results Summary
[Link to **working** workflow run results](sampleURL:https://github.com/WSU-kduncan/s24cicd-pattonsgirl/actions/runs/8726150186/job/23941797523)
