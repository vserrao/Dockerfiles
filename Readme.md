This repository contains Dockerfiles to install and configure the dependencies for few opensoure tools. The instructions to build the Dockerfiles into an image are provided per Dockerfile in it's own Readme.md file. After building the image from this Dockerfile, create a container. The user then only requires to clone respective package from github and start working with it. This saves the developer's time from the hassles in getting the dependencies setup.

Note: As per our usecase, the local jenkins user id is mapped to the jenkins user that will be created through the Dockerfiles. If the use of jenkins user is not required, then the developer may skip/comment out the 'Setup jenkins' steps and the 'RUN usermod....' instruction and create a custom user or continue as root user, as per you usecase needs.

Happy working!!
