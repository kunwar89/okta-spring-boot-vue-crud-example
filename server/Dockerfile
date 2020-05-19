FROM openjdk:8 AS BUILD_IMAGE
ENV APP_HOME=/root/dev/myapp/
RUN mkdir -p $APP_HOME/src/main/java
WORKDIR $APP_HOME
COPY /server/build.gradle /server/gradlew /server/gradlew.bat $APP_HOME
COPY /server/gradle $APP_HOME/gradle
# download dependencies
COPY . .
RUN ./gradlew build --stacktrace --debug --info

#RUN ./gradlew build
# EXPOSE 8080
# CMD ["java","-jar","/root/dev/myapp/build/libs/myapp.jar"]
