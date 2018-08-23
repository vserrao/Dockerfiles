#Download parent image centos 7
FROM ppc64le/centos:7
MAINTAINER Valencia Serrao <vserrao@us.ibm.com>

#Update OS repositories and install dependencies
RUN yum update -y && \
    yum install -y \
    git \
    java-1.8.0-openjdk-devel.i686 \
    vim \
    wget && \
    #Setup maven-3.5.4
    cd /opt && \
    wget http://www-eu.apache.org/dist/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz && \
    tar -xvf apache-maven-3.5.4-bin.tar.gz && \
    ln -s apache-maven-3.5.4 apache-maven && \
    #Setup jenkins
    wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo && \
    rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key && \
    yum install -y jenkins

#Setup env variables
ENV MAVEN_HOME /opt/apache-maven
ENV PATH ${MAVEN_HOME}/bin:${PATH}

RUN usermod -u 973 jenkins && groupmod -g 949 jenkins

USER jenkins

WORKDIR /var/lib/jenkins

RUN echo "Dependency for Knox pkg are setup successfully for the following config: \n && \
          OS: RHEL 7 \n && \
          Arch: ppc64le \n && \
          You may clone the Knox github repo now \n" && \
    rm -rf *
