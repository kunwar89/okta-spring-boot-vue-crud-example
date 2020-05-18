FROM openjdk:8 AS BUILD_IMAGE
ENV APP_HOME_PATH=/root/dev/myapp/
RUN mkdir -p $APP_HOME_PATH/src/main/java
WORKDIR $APP_HOME_PATH
COPY build.gradle gradlew gradlew.bat $APP_HOME_PATH
COPY gradle $APP_HOME_PATH/gradle
# download dependencies
RUN ./gradlew build
FROM openjdk:8-jre
WORKDIR /root/
COPY --from=BUILD_IMAGE /root/dev/myapp/build/libs/myapp.jar .
EXPOSE 8080
CMD ["java","-jar","myapp.jar"]
