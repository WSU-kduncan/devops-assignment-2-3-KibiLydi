# DevOps Assigment 2 - GitHub Actions & DockerHub

## Description of Workflow

So, obviously the original code was already extensively commented, and I kinda just copy/pasted the file over here. I'm going to try to explain what the workflow is doing in my own words. There are 3 main jobs:

### Compile the WorkOrder Pro Springboot application to a Java JAR
This part of the yaml is the compilation process for the java project, obviously. The workflow first needs to actually install the JDK in order to compile it. This is because the operating system that the job is executed in is essentially a fresh build of Ubuntu. Once the JDK is installed, the job uses gradlew to build it into a JAR file. The code also renames the .jar to "app.jar" and creates an artifact for the job it just completed. The original build.yml had a version that was too old for this project, so I changed the version from 11 to 17.

### Build the JAR application into a docker image
This section first installs a fresh install of ubuntu, which will be used to run the docker image. The code has to make sure that the installation successfully completed before it makes an image; this has to be explicitly programmed in because jobs run in parallel by default. It creates the image using the credentials of the user's Dockerhub account, which have already been added as a Secret into the GitHub repository. It does this dynamically so that it will automatically change for the user running the action.

### Push the Docker image to your account on GitHub
After all this, it finally builds the image and pushes it to the specified GitHub repository. It uses the assignment repository, and marks it with the commit's hash. GitHub will automatically run the action.

## Link to DockerHub Repository
[DockerHub - `CLARK-WOPro-Service`](https://github.com/WSU-kduncan/devops-assignment-2-3-KibiLydi)

## Link to GitHub Actions Run Results Summary
[Link to **working** workflow run results](https://github.com/WSU-kduncan/devops-assignment-2-3-KibiLydi/actions/runs/11654488394)
