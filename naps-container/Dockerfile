FROM centos
MAINTAINER BN Ratna Kumar, ngratnakumar@gmail.com, NAPS Container [Centos 7, Glassfish 4.1.1, PostgreSQL 9.4.10, Latex]

ENV JAVA_VERSION 8u31
ENV BUILD_VERSION b13

# Upgrading system
RUN yum -y upgrade
RUN yum -y install wget unzip

# fix for NOKEY issue, by installing key
RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-Debug-7
RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-Testing-7

# Downloading Java
RUN wget --no-cookies --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/$JAVA_VERSION-$BUILD_VERSION/jdk-$JAVA_VERSION-linux-x64.rpm" -O /tmp/jdk-8-linux-x64.rpm

RUN yum -y install /tmp/jdk-8-linux-x64.rpm 

RUN alternatives --install /usr/bin/java jar /usr/java/latest/bin/java 200000
RUN alternatives --install /usr/bin/javaws javaws /usr/java/latest/bin/javaws 200000
RUN alternatives --install /usr/bin/javac javac /usr/java/latest/bin/javac 200000

ENV JAVA_HOME /usr/java/latest

# Downloading glassfish 4.1.1
RUN /bin/wget http://download.java.net/glassfish/4.1.1/release/glassfish-4.1.1.zip

# Extracting glassfish
RUN /bin/unzip glassfish-4.1.1.zip

# Installing Postgresql94
# RUN yum -y install postgresql94

# Running tomee server - port 8080
# CMD /bin/bash apache-tomee-plume-7.0.2/bin/startup.sh && /bin/bash
CMD /bin/bash