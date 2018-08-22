#Download parent image ubuntu 18.04
FROM ubuntu:18.04
MAINTAINER Valencia Serrao <vserrao@us.ibm.com>

#Update OS repositories and install dependencies
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y \
    ant \
    apt-transport-https \
    git \
    gnupg \
    openjdk-8-jdk \
    vim \
    wget && \
    #Setup jenkins
    wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | apt-key add - && \
    sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list' && \
    apt-get -y update && \
    apt-get install -y jenkins

RUN usermod -u 973 jenkins && groupmod -g 949 jenkins

USER jenkins

WORKDIR /var/lib/jenkins

RUN echo "Dependency for Zookeeper pkg are setup successfully for the following config: \n && \
          OS: Ubuntu18.04 \n && \
          Arch: x86_64 \n && \
          You may clone the Zookeeper github repo now\n" && \
    rm -rf *
