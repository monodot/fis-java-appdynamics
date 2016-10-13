FROM registry.access.redhat.com/jboss-webserver-3/webserver30-tomcat8-openshift

USER root

ADD appdynamics/ /opt/appdynamics/

RUN chown -R jboss:jboss /opt/appdynamics/
RUN chmod -R g+rw /opt/appdynamics/
RUN find /opt/appdynamics/ -type d -exec chmod g+x {} +
RUN mkdir /deployments/logs

ENV JAVA_OPTS="-javaagent:/opt/appdynamics/javaagent.jar -Dappdynamics.agent.logs.dir=/deployments/logs ${JAVA_OPTS}" \
    JBOSS_IMAGE_NAME="webserver30-tomcat8-appdynamics" \
    JBOSS_IMAGE_VERSION="1.0" \

#jboss from FIS
USER 185
