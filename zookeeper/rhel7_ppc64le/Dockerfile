#Download parent image centos 7
FROM ppc64le/centos
MAINTAINER Valencia Serrao <vserrao@us.ibm.com>

#Update OS repositories and install dependencies
RUN yum -y update && \
    yum install -y \
    ant \
    ant-junit.noarch \
    git \
    java-1.8.0-openjdk-devel.ppc64le \
    vim \
    wget && \
    #Setup jenkins
    wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo && \
    rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key && \
    yum install -y jenkins

RUN usermod -u 109 jenkins && groupmod -g 117 jenkins

USER jenkins

WORKDIR /var/lib/jenkins

RUN echo "Dependency for Zookeeper pkg are setup successfully for the following config: \n && \
          OS: Rhel 7 \n && \
          Arch: ppc64le \n && \
          You may clone the Zookeeper github repo now \n" && \
    rm -rf *
