FROM openjdk:8-jdk

#
# Install Zookeeper
#
ENV ZOOKEEPER_MIRROR=https://archive.apache.org/dist/zookeeper \
    ZOOKEEPER_VERSION=3.4.11

RUN apt-get update                                                                                    && \
    apt-get -y install ca-certificates                                                                && \
    wget -q   $ZOOKEEPER_MIRROR/zookeeper-$ZOOKEEPER_VERSION/zookeeper-$ZOOKEEPER_VERSION.tar.gz.md5  && \
    wget -q   $ZOOKEEPER_MIRROR/zookeeper-$ZOOKEEPER_VERSION/zookeeper-$ZOOKEEPER_VERSION.tar.gz      && \
    md5sum -c zookeeper-$ZOOKEEPER_VERSION.tar.gz.md5                                                 && \
    tar xzf   zookeeper-$ZOOKEEPER_VERSION.tar.gz                                                     && \
    rm        /zookeeper-$ZOOKEEPER_VERSION.tar.gz*                                                   && \
    mv        /zookeeper-$ZOOKEEPER_VERSION /zookeeper

EXPOSE 2181 2888 3888

#
# Install Exhibitor
#
ENV EXHIBITOR_VERSION=1.7.0 \
    EXHIBITOR_POM_URL=https://raw.githubusercontent.com/soabase/exhibitor/exhibitor-$EXHIBITOR_VERSION/exhibitor-standalone/src/main/resources/buildscripts/standalone/maven/pom.xml

RUN mkdir /exhibitor                                                  && \
    cd    /exhibitor                                                  && \
    apt-get -y install maven                                          && \
    wget -q $EXHIBITOR_POM_URL                                        && \
    mvn clean package                                                 && \
    mv /exhibitor/target/exhibitor-1.6.0.jar /exhibitor/              && \
    rm -rf exhibitor/pom.xml /exhibitor/target/ /root/.m2/            && \
    apt-get -y remove maven

EXPOSE 8080
