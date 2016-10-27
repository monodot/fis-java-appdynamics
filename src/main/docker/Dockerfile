FROM registry.access.redhat.com/jboss-webserver-3/webserver30-tomcat8-openshift:1.2

USER root

ADD appdynamics/ /opt/appdynamics/
COPY usr/local/bin/ /usr/local/bin/

RUN /usr/local/bin/fix-permissions.sh /usr/local/bin \
  && /usr/local/bin/fix-permissions.sh /opt/appdynamics \
  && chmod 775 /usr/local/bin/* \
  && chown -R jboss:jboss /opt/appdynamics

ENV JAVA_OPTS="-javaagent:/opt/appdynamics/javaagent.jar -Dappdynamics.agent.logs.dir=/opt/webserver/logs ${JAVA_OPTS}" \
    JBOSS_IMAGE_NAME="webserver30-tomcat8-appdynamics" \
    JBOSS_IMAGE_VERSION="1.2.appdynamics"

#jboss from FIS
USER 185
