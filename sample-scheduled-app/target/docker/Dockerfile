FROM frolvlad/alpine-oraclejdk8:slim
ADD /sample-scheduled-app-1.0-SNAPSHOT.jar //
ENTRYPOINT ["java", "-Xmx512m","-Djava.security.egd=file:/dev/./urandom", "-jar", "/sample-scheduled-app-1.0-SNAPSHOT.jar"]
