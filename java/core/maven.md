# Maven

## Quick start

```sh
mvn archetype:generate -DgroupId=com.example.app -DartifactId=core-java -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

## Reload maven project

```sh
mvn clean package
```

## Compile offline

```sh
 mvn clean package -o  
```