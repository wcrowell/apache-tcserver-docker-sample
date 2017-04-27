FROM centos:7
EXPOSE 6969 8009 8080 8443

RUN yum install -y vim wget java git

# install yum repo
#RUN rpm --import http://packages.gopivotal.com/pub/rpm/rhel6/app-suite/RPM-GPG-KEY-PIVOTAL-APP-SUITE-EL6
RUN rpm --import http://packages.gopivotal.com/pub/rpm/rhel7/app-suite/RPM-GPG-KEY-PIVOTAL-APP-SUITE-EL7
RUN yum-config-manager --add-repo http://packages.pivotal.io/pub/rpm/rhel7/app-suite/x86_64

# install tcserver
RUN yum install -y pivotal-tc-server-standard

# set JAVA_HOME to the java version installed by yum
RUN cd ~
ENV JAVA_HOME /usr

# install tcserver instance (01)
RUN mkdir -p /web/tcserver
RUN /opt/pivotal/pivotal-tc-server-standard/tcruntime-instance.sh create -i /web/tcserver 01

# add a set of roles and users to test login with.
ADD tomcat-users.xml /web/tcserver/01/conf

# add an AJP 1.3 connector running on port 8009. 
ADD server.xml /web/tcserver/01/conf

# start the tcserver instance which will be PID 1
ENTRYPOINT ["/web/tcserver/01/bin/tcruntime-ctl.sh", "run"]

