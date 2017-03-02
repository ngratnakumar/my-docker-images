FROM centos
MAINTAINER BN Ratna Kumar, ngratnakumar@gmail.com

ENV JAVA_VERSION 8u31
ENV BUILD_VERSION b13

# Upgrading system
RUN yum -y upgrade
RUN yum -y install wget tar

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

# Downloading tomee
RUN /bin/wget http://repo.maven.apache.org/maven2/org/apache/tomee/apache-tomee/7.0.2/apache-tomee-7.0.2-plume.tar.gz

# Extracting tomee
RUN /bin/tar -xvf apache-tomee-7.0.2-plume.tar.gz

# Downloading NodeJs 7.x
# ========================================================================*/
RUN /bin/curl -sL https://rpm.nodesource.com/setup_7.x | /bin/bash -

# Installling npm and dependencies
RUN yum -y --nogpgcheck install nodejs vim-minimal.x86_64
# RUN yum -y install gcc-c++ make
# ========================================================================*/

# Running tomee server - port 8080
CMD /bin/bash apache-tomee-plume-7.0.2/bin/startup.sh && /bin/bash