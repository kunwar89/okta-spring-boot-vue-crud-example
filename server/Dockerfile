FROM openjdk:8 AS BUILD_IMAGE
ENV APP_HOME=/github/workspace
RUN mkdir -p $APP_HOME/src/main/java
WORKDIR $APP_HOME
COPY /source/okta-spring-boot-vue-crud-example/server/build.gradle /source/okta-spring-boot-vue-crud-example/server/gradlew /source/okta-spring-boot-vue-crud-example/server/gradlew.bat $APP_HOME
COPY /source/okta-spring-boot-vue-crud-example/gradle $APP_HOME/gradle
# download dependencies
COPY . .
RUN ./gradlew build
FROM openjdk:8-jre
WORKDIR /root/
COPY --from=BUILD_IMAGE $APP_HOME/build/libs/myapp.jar .
EXPOSE 8080
CMD ["java","-jar","myapp.jar"]
