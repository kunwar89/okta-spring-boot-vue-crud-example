FROM openjdk:8 AS BUILD_IMAGE
ENV HOME
RUN mkdir -p $HOME/src/main/java
WORKDIR $HOME
COPY build.gradle gradlew gradlew.bat $APP_HOME_PATH
COPY gradle $HOME/gradle
# download dependencies
RUN ./gradlew build
FROM openjdk:8-jre
WORKDIR /root/
COPY --from=BUILD_IMAGE /root/dev/myapp/build/libs/myapp.jar .
EXPOSE 8080
CMD ["java","-jar","myapp.jar"]
