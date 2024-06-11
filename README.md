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

### Configuring Git

1. Configure your identity and default editor:
    ```sh
    git config --global user.name "John Doe"
    git config --global user.email johndoe@example.com
    git config --global core.editor emacs
    ```

    Review your configuration:
    ```sh
    git config --list
    ```
    Should return something like:
    ```sh
    user.name=John Doe
    user.email=johndoe@example.com
    core.editor=emacs
    ```

2. Create a Git repository:
    ```sh
    git init
    ```

    Should display:
    ```sh
    Initialized empty Git repository in /path/to/your/repo/.git/
    ```

3. Add files to version control:
    ```sh
    git add pom.xml
    git status
    ```

4. Commit changes and create a new version:
    ```sh
    git commit -m 'First version of the project'
    ```

    Should display something like:
    ```sh
    [master (root-commit) b75ab28] First version of the project
    1 file changed, 40 insertions(+)
    create mode 100644 pom.xml
    ```

5. Work with remote repositories:
    - Create a repository on GitHub.
    - Add the remote repository:
        ```sh
        git remote add origin https://github.com/yourusername/yourrepo.git
        ```

    - Verify the configuration:
        ```sh
        git remote
        git remote -v
        ```

    - Push the latest version of the project to the remote repository:
        ```sh
        git push -u origin master
        ```

        Should display something like:
        ```sh
        Username for 'https://github.com': yourusername
        Password for 'https://yourusername@github.com':
        Counting objects: 3, done.
        Delta compression using up to 4 threads.
        Compressing objects: 100% (2/2), done.
        Writing objects: 100% (3/3), 624 bytes | 0 bytes/s, done.
        Total 3 (delta 0), reused 0 (delta 0)
        To https://github.com/yourusername/yourrepo.git
        * [new branch] master -> master
        Branch master set up to track remote branch master from origin.
        ```

6. Add more files to your project and remote repository:
    - Create README, LICENSE, and .gitignore files:
        ```sh
        echo 'My first project' > README.txt
        echo 'TODO: Copy the license text from http://www.gnu.org/licenses/gpl.html' > LICENSE.txt
        echo '# TODO: Copy contents from https://github.com/github/gitignore/blob/master/Java.gitignore' > .gitignore
        ```

    - Add the files:
        ```sh
        git add *.txt
        git add .gitignore
        ```

    - Add the src directory and its content:
        ```sh
        git add src
        ```

    - Review the status of your project:
        ```sh
        git status -s
        ```

    - Modify .gitignore to exclude the target directory:
        ```sh
        echo 'target/' >> .gitignore
        git add .gitignore
        ```

    - Commit the changes and push them to the remote repository:
        ```sh
        git commit -m 'Second version of the project, adding and ignoring more files'
        git push
        ```

    - To get the latest changes from the remote repository:
        ```sh
        git pull
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


