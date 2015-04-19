FROM centos:centos7
MAINTAINER "Christian Kniep <christian@qnib.org>"

RUN rpm --import https://packages.elasticsearch.org/GPG-KEY-elasticsearch
ADD etc/yum.repos.d/logstash.repo /etc/yum.repos.d/logstash.repo
RUN yum install -y logstash
RUN yum install -y git-core
RUN yum install -y vim wget tar 
RUN yum install -y epel-release && \
    yum install -y python-zmq
ENV JRUBY_VER 1.7.19
RUN wget -q https://s3.amazonaws.com/jruby.org/downloads/${JRUBY_VER}/jruby-bin-${JRUBY_VER}.tar.gz && \
    tar xfz jruby-bin-${JRUBY_VER}.tar.gz && \
    mv jruby-${JRUBY_VER} /opt/ && \
    rm -f jruby-bin-${JRUBY_VER}.tar.gz
RUN echo "PATH=$PATH:/opt/jruby-${JRUBY_VER}/bin" > /etc/profile.d/jruby.sh && \
    echo "JRUBY_HOME=/opt/jruby-${JRUBY_VER}/" >> /etc/profile.d/jruby.sh
RUN yum install -y czmq-devel



ADD run.sh /opt/
CMD ["/opt/run.sh"]
