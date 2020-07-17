# Maven

## Walkthrough

### Creating a Java Project

Run the command:

```text
$ mvn archetype:generate \
  -DgroupId=com.alexius \
  -DartifactId=helloworld \
  -DarchetypeArtifactId=maven-archetype-quickstart \
  -DinteractiveMode=false
```

The `artifactID` is the name of the project. Hence, after the project is created, you can simply go inside the directory: `/helloworld`.

> Hint: In order to create web App, change the archetype artifact ID value into `maven-archetype-webapp`.

The format of the command is shown as follows:

```text
$ mvn <plugin>:<goal> -D<parameters>=<value>
```

By default, Maven doesn't know how it could create the project. It does it by means of the plugins.

### POM File

The POM file will contain information with the XML format:

```markup
<project
  xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd"
>
  <modelVersion>4.0.0</modelVersion>
  
  <!-- The following 4 fields are belongs to Maven coordinates. -->
  <groupId>com.alexius</groupId>
  <artifactId>helloworld</artifactId>
  <packaging>jar</packaging>
  <version>1.0-SNAPSHOT</version>
  
  <name>helloworld</name>
  <url>http://maven.apache.org</url>
  
  <!-- Libraries included in this project -->
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```

> You might need to include the compiler source and target version configuration:
>
> ```markup
> <project>
>   <!-- ... -->
>
>   <properties>
>     <maven.compiler.source>3.8.1</maven.compiler.source>
>     <maven.compiler.target>3.8.1</maven.compiler.target>
>   </properties>
>   
>   <!-- ... -->
> </project>
> ```

### Maven Coordinates

* Group ID: the name of the organization or company which the project belongs to.
* Artifact ID: the name of the project.
* Version
* Packaging: the type of the project application, for instance, `jar` or `war`

### Running the Project

Simply run install:

```text
$ mvn install
```

After compilation success, we can execute the compiled result:

```text
$ java -cp target/helloworld-<SNAPSHOT>.jar com.alexius.App
```

It follows the pattern where the compiled result would be a `.jar` file inside the `target` folder followed by the target class.

When Maven runs the installation process, it will fetch the dependencies.

{% embed url="https://mvnrepository.com/" %}



