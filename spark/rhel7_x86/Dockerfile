#Download parent image centos 7
FROM centos:7
MAINTAINER Valencia Serrao <vserrao@us.ibm.com>

#Update OS repositories and install dependencies
RUN yum -y update && \
    yum install -y \
    vim \
    wget \
    git \
    java-1.8.0-openjdk-devel.i686 && \
    #Setup maven-3.5.4
    cd /opt && wget http://www-eu.apache.org/dist/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz && \
    tar -xvf apache-maven-3.5.4-bin.tar.gz && \
    ln -s apache-maven-3.5.4 apache-maven && \
    #Setup Jenkins
    wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo && \
    rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key && \
    yum install -y jenkins

ENV MAVEN_HOME /opt/apache-maven
ENV PATH ${MAVEN_HOME}/bin:${PATH}

RUN usermod -u 973 jenkins && groupmod -g 949 jenkins

USER jenkins

WORKDIR /var/lib/jenkins

RUN echo "Dependency for Spark pkg are setup successfully for the following config: \n && \
          OS: RHEL 7 \n && \
          Arch: x86_64 \n && \
          You may clone the Spark github repo now\n" && \
    rm -rf *
