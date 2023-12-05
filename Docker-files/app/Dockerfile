FROM openjdk:11 AS build_image
LABEL "Project"="Vprofile"
LABEL "Author"="Amr"
RUN apt update && apt install maven -y
RUN git clone https://github.com/afarag2010/vprofile-project.git 
RUN cd vprofile-project && git checkout docker && mvn install



FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Amr"
RUN rm -rf /usr/local/tmocat/webapps/*
COPY --from=build_image vprofile-project/target/vprofile-v2.war /usr/local/tmocat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh","run"]
WORKDIR /usr/local/webapps/
