FROM gradle:7 AS Base
CMD ["bash"]


#build
FROM Base AS build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build


#product
FROM openjdk:17 AS production
COPY --from=test-and-build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./app.jar
CMD [ "java", "-jar", "app.jar" ]
