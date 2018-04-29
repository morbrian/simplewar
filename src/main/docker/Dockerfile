FROM registry.access.redhat.com/jboss-webserver-3/webserver31-tomcat8-openshift

USER root

RUN rm -Rf /opt/webserver/webapps/*; \
    rm -f /opt/webserver/lib/mongo.jar /opt/webserver/lib/mysql-connector-java.jar; \
    rm -Rf /opt/rh/rh-maven* /opt/rh/rh-mongodb*; \
    mkdir -p /opt/webserver/conf/Catalina/localhost; \
    chmod 770 /opt/webserver/conf/Catalina/localhost; \
    mkdir /artifact;

COPY ROOT.xml /opt/webserver/conf/Catalina/localhost/ROOT.xml
COPY maven/ROOT.war /artifact/ROOT.war

RUN chmod -R 770 /artifact; \
    chmod -R 770 /opt/webserver/conf/Catalina/localhost

USER jboss
CMD /opt/webserver/bin/launch.sh

