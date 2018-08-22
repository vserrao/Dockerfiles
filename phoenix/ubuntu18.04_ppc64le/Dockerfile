#Download parent image ubuntu 18.04
FROM ppc64le/ubuntu:18.04
MAINTAINER Valencia Serrao <vserrao@us.ibm.com>

#Update OS repositories and install dependencies
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -y update && \
    apt-get install -y \
    apt-transport-https \
    gnupg \
    git \
    krb5-user \
    openjdk-8-jdk \
    wget \
    vim && \
    #Setup maven
    cd /opt && wget http://www-eu.apache.org/dist/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz && \
    tar -xvf apache-maven-3.5.4-bin.tar.gz && \
    ln -s apache-maven-3.5.4 apache-maven && \
    #Setup jenkins
    wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | apt-key add - && \
    sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list' && \
    apt-get -y update && \
    apt-get install -y jenkins

#Setup env variables
ENV MAVEN_HOME /opt/apache-maven
ENV PATH ${MAVEN_HOME}/bin:${PATH}

RUN usermod -u 109 jenkins && groupmod -g 117 jenkins

USER jenkins
 
WORKDIR /var/lib/jenkins

RUN echo "Dependency for Phoenix pkg are setup successfully for the following config: \n && \
          OS: Ubuntu18.04\n && \
          Arch: ppc64le\n && \
          You may clone the Phoenix github repo now\n" && \
   rm -rf *
