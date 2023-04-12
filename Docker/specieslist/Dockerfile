# FROM openjdk:8-jdk-alpine
# From https://github.com/bioatlas/ala-docker/blob/master/specieslists/Dockerfile
FROM tomcat:8-jre8-temurin

ARG ENV

RUN apk --no-cache add curl
RUN mkdir -p /data/specieslist-webapp/config
RUN rm -r ${CATALINA_HOME}/webapps/ROOT \
    && rm -r ${CATALINA_HOME}/webapps/docs \
    && rm -r ${CATALINA_HOME}/webapps/examples \
    && rm -r ${CATALINA_HOME}/webapps/host-manager \
    && rm -r ${CATALINA_HOME}/webapps/manager

RUN curl -o specieslist-webapp.war "https://nexus.ala.org.au/service/local/repositories/releases/content/au/org/ala/specieslist-webapp/4.0.4/specieslist-webapp-4.0.4.war"
COPY specieslist-webapp.war $CATALINA_HOME/webapps/ROOT.war

ENV \
    BUILD_DEPS="gettext" \
    RUNTIME_DEPS="libintl"

RUN \
    apk add --update $RUNTIME_DEPS && \
    apk add --virtual build_deps $BUILD_DEPS &&  \
    cp /usr/bin/envsubst /usr/local/bin/envsubst && \
    apk del build_deps

RUN apk add --update tini
ENTRYPOINT ["tini", "--"]
CMD ["catalina.sh", "run"]