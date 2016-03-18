FROM 192.168.1.110:5000/tomcat:7

MAINTAINER "huangzq@asiainfo.com"

RUN mkdir -p /code
WORKDIR /code

ADD docker-web/src /code/src
ADD docker-web/pom.xml /code/pom.xml

# edit settings.xml
RUN rm -r $MAVEN_HOME/conf/settings.xml

ADD docker-web/settings.xml $MAVEN_HOME/conf/settings.xml

# bulid project
RUN mvn clean install package

# clean maven rep
RUN rm -rf /usr/.m2/repository

RUN yes|cp target/*.war $CATALINA_HOME/webapps

RUN rm -rf /code



