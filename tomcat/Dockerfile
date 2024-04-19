FROM openjdk:11-jre-slim

RUN apt-get update && \
    apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/*

ENV TOMCAT_VERSION 8.5.100
ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH

RUN wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.100/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz && \
    tar -xf apache-tomcat-${TOMCAT_VERSION}.tar.gz && \
    mv apache-tomcat-${TOMCAT_VERSION} $CATALINA_HOME && \
    rm apache-tomcat-${TOMCAT_VERSION}.tar.gz

RUN wget https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.20.0/jmx_prometheus_javaagent-0.20.0.jar && \
    mv jmx_prometheus_javaagent-0.20.0.jar /tmp

# Configuration files
COPY ./tomcat-users.xml ${CATALINA_HOME}/conf/
COPY ./context.xml ${CATALINA_HOME}/webapps/manager/META-INF/
COPY ./setenv.sh ${CATALINA_HOME}/bin
COPY ./config.yml /tmp

# Sample project WAR
RUN wget -O ${CATALINA_HOME}/webapps/sample.war https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/sample.war

EXPOSE 8080 8088

CMD ["catalina.sh", "run"]
