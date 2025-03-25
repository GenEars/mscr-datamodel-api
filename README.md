# yti-datamodel-api

Interoperability workbench data model editor backend

## Requirements
- Java 17
- Docker
- Gradle 7.6

## Development

### Checkout library projects
- [yti-spring-migration](https://github.com/VRK-YTI/yti-spring-migration): Framework for implementing persistent layer migrations
- [yti-spring-security](https://github.com/VRK-YTI/yti-spring-security): Shared spring security config between applications

Checkout corresponding tag for version defined in build.gradle, e.g. `git checkout v0.2.0`
Install package to local maven repository `./gradlew publishToMavenLocal`

### Checkout other required projects
- [yti-groupmanagement](https://github.com/VRK-YTI/yti-groupmanagement)
- [yti-fuseki](https://github.com/VRK-YTI/yti-fuseki): Custom fuseki container build for YTI

For each project run `build.sh` located at the project root folder. The script builds a docker image for the project.

### Checkout yti-compose project

Start dependant containers
```
docker-compose up -d yti-groupmanagement yti-fuseki-v4 yti-datamodel-opensearch
```

Copy content from main/resources/config/application.properties.template to file application-local.properties and adjust values as needed.

### Populate data to the database
```
./src/scripts/init.admin.sh
```

## API docs
http://localhost:9004/datamodel-api/swagger-ui/index.html
