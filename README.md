# Introduction to Maven, Git, and GitHub

This project provides an introductory guide on how to use Maven, Git, and GitHub to automate and standardize the workflow in software construction and version control.

## Getting Started

These instructions will help you get a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

You need to install the following tools and configure their dependencies:

1. **Java** (versions 7 or 8)
    ```sh
    java -version
    ```
    Should return something like:
    ```sh
    java version "1.8.0"
    Java(TM) SE Runtime Environment (build 1.8.0-b132)
    Java HotSpot(TM) 64-Bit Server VM (build 25.0-b70, mixed mode)
    ```

2. **Maven**
    - Download Maven from [here](http://maven.apache.org/download.html)
    - Follow the installation instructions [here](http://maven.apache.org/download.html#Installation)

    Verify the installation:
    ```sh
    mvn -version
    ```
    Should return something like:
    ```sh
    Apache Maven 3.2.5 (12a6b3acb947671f09b81f49094c53f426d8cea1; 2014-12-14T12:29:23-05:00)
    Maven home: /Users/dnielben/Applications/apache-maven-3.2.5
    Java version: 1.8.0, vendor: Oracle Corporation
    Java home: /Library/Java/JavaVirtualMachines/jdk1.8.0.jdk/Contents/Home/jre
    Default locale: es_ES, platform encoding: UTF-8
    OS name: "mac os x", version: "10.10.1", arch: "x86_64", family: "mac"
    ```

3. **Git**
    - Install Git by following the instructions [here](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

    Verify the installation:
    ```sh
    git --version
    ```
    Should return something like:
    ```sh
    git version 2.2.1
    ```

### Installing

Step-by-step series to get your development environment running:

1. Open a terminal and navigate to the directory where you will store your projects:
    ```sh
    mvn archetype:generate -DgroupId=edu.escuelaing.arsw.ASE.app -DartifactId=miprimera-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
    cd mi-primera-app/
    ```

2. Source code for `App.java`:
    ```java
    package edu.escuelaing.app;

    /**
    * Hello world!
    *
    */
    public class App {
        public static void main(String[] args) {
            System.out.println("Hello World!");
        }
    }
    ```

3. Configuration for `pom.xml`:
    ```xml
    <project xmlns="http://maven.apache.org/POM/4.0.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>edu.escuelaing.app</groupId>
        <artifactId>mi-primera-app</artifactId>
        <packaging>jar</packaging>
        <version>1.0-SNAPSHOT</version>
        <name>mi-primera-app</name>
        <url>http://maven.apache.org</url>
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

4. Build the project:
    ```sh
    mvn package
    ```

    Should display output similar to:
    ```sh
    [INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ mi-primera-app ---
    [INFO] Building jar: /Users/dnielben/NetBeansProjects/mi-primera-app/target/mi-primera-app-1.0-SNAPSHOT.jar
    [INFO] BUILD SUCCESS
    ```

5. Run the application:
    ```sh
    java -cp target/mi-primera-app-1.0-SNAPSHOT.jar edu.escuelaing.app.App
    ```

    The output should be:
    ```sh
    Hello World!
    ```


## Built With

* [Maven](https://maven.apache.org/) - Dependency Management
* [Git](http://git-scm.com/) - Version Control System



## Versioning

I use [GitHub](https://github.com/) for versioning. For the versions available, see the [tags on this repository](https://github.com/alexandrac1420/ARSW_Lab01).

## Authors

* **Alexandra Cortes Tovar** - [alexandrac1420](https://github.com/alexandrac1420)


## License

This project is licensed under the GNU License - see the [LICENSE.md](LICENSE.md) file for details.


