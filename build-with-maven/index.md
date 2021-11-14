---
title: 13 - Build With Maven
nav_order: 13
has_children: true
nav_exclude: false
---

# Lesson 19: Build With Maven

## Goals

- Build jar
- Build executable jar

## Maven Build Lifecycle

See [**Maven Build Lifecycle**](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)

The default lifecycle comprises the following phases:

1. `validate` - validate the project is correct and all necessary information is available
2. `compile`- compile the source code of the project
3. `test` - test the compiled source code using a suitable unit testing framework. These tests should not require the
   code be packaged or deployed
4. `package` - take the compiled code and package it in its distributable format, such as a JAR.
5. `verify` - run any checks on results of integration tests to ensure quality criteria are met
6. `install` - install the package into the local repository, for use as a dependency in other projects locally
7. `deploy` - done in the build environment, copies the final package to the remote repository for sharing with other
   developers and projects.

These lifecycle phases (plus the other lifecycle phases not shown here) are executed sequentially to complete the
default lifecycle. Given the lifecycle phases above, this means that when the default lifecycle is used, Maven will
first validate the project, then will try to compile the sources, run those against the tests, package the binaries (
e.g. jar), run integration tests against that package, verify the integration tests, install the verified package to the
local repository, then deploy the installed package to a remote repository.

In most of the cases you would only need to execute the following:

```
mvn clean verify
```

1. `clean` - to delete any previous build so that a fresh build can be done
2. `verify` - to execute the build lifecycle from `validate` to `verify`

## Install Maven

For Mac users, if you have `brew` installed you can simply execute `brew install maven` to have maven on your machine.

Otherwise, follow these instructions

1. [Downloading Apache Maven 3.8.3](https://maven.apache.org/download.cgi)
    - Here, you will download a compressed file that contains the maven distribution.
2. [Extract the downloaded archive](https://maven.apache.org/install.html)
    1. It is important that you extract the archive downloaded into a directory that is not easily deleted.
    2. Mac/Linux `/opt/apache-maven-3.8.3`
    3. Windows`C:\Program Files\apache-maven-3.8.3`
3. Add the `bin` directory of the extracted directory `apache-maven-3.8.3` to the `PATH` environment variable
    1. Mac/Linux
        1. [See how to set an environment variable](https://stackoverflow.com/a/31546962)
            ```
            export PATH=/opt/apache-maven-3.8.3/bin:$PATH
            ```
        2. Start a new terminal and verify the `PATH` with `echo PATH`
    2. Windows
        1. [See how to set an environment variable](https://maven.apache.org/install.html#windows-tips)
        2. Append the directory to the existing `PATH`
        3. Start a new terminal and verify the `PATH` with `echo %PATH%`
4. Set or verify the `JAVA_HOME` environment variable using the same method above
5. Open a new terminal and run `mvn -v` to verify the installation.

## Maven Project: An Application that generates QR Code

1. Create a new maven project on Intellij.
2. Verify project can build `mvn clean verify`
3. [Set Java Version For New Project](https://maven.apache.org/plugins/maven-compiler-plugin/examples/set-compiler-source-and-target.html)
4. Create a package (`com.redi.maven`)
5. Create an `Application` class with a `main` method that prints `Hello world!`.
6. Set the main class for the executable jar plugin

      ```xml
    
    <build>
        ....
        <plugins>
            ....
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <configuration>
                    <archive>
                        <manifest>
                            <mainClass>com.redi.maven.Application</mainClass>
                        </manifest>
                    </archive>
                </configuration>
            </plugin>
            ....
        </plugins>
        ....
    </build>
      ```

7. Verify project can build `mvn clean verify`
8. Execute the resulting jar file `java -jar target/maven-demo-1.0-SNAPSHOT.jar`
9. Add dependency for [ZXing](https://zxing.github.io/zxing/project-info.html) which will be used to generate QR Codes
    
      ```xml
    
    <dependencies>
        .....
        <dependency>
            <groupId>com.google.zxing</groupId>
            <artifactId>core</artifactId>
            <version>3.4.1</version>
        </dependency>
        <dependency>
            <groupId>com.google.zxing</groupId>
            <artifactId>javase</artifactId>
            <version>3.4.1</version>
        </dependency>
        ....
    </dependencies>
      ```

10. Add code to generate QR Code

      ```java
    final String text=args.length>0?args[0]:"dummy";
    final int size=args.length>1?Integer.parseInt(args[1]):100;
    final BitMatrix result=new MultiFormatWriter().encode(text,BarcodeFormat.QR_CODE,size,size,null);
    final BufferedImage image=MatrixToImageWriter.toBufferedImage(result);
    final File outputfile=new File(text+".jpg");
    ImageIO.write(image,"jpg",outputfile);
      ```

11. Execute using IntelliJ and inspect the generated QR Code.
12. Verify project can build `mvn clean verify`
13. Execute the resulting jar file with some arguments
      ```
        java -jar target/maven-demo-1.0-SNAPSHOT.jar "Hello World!" 250
      ```
    to generate a QR Code for the text `"Hello World!"`, having a width of 250 pixels.

14. Exception because not all classes and libraries are included in the jar file
      ```
      Error: Unable to initialize main class com.redi.maven.Application
      Caused by: java.lang.NoClassDefFoundError: com/google/zxing/WriterException
      ```

15. Building an executable jar with all dependencies. This is only needed if you want to ship an application that needs
    to be executed standalone. Add the maven assembly plugin to enable packaging jar with dependencies
      ```xml
    
    <plugin>
        <artifactId>maven-assembly-plugin</artifactId>
        <configuration>
            <archive>
                <manifest>
                    <mainClass>com.redi.maven.Application</mainClass>
                </manifest>
            </archive>
            <descriptorRefs>
                <descriptorRef>jar-with-dependencies</descriptorRef>
            </descriptorRefs>
        </configuration>
        <executions>
            <execution>
                <id>make-assembly</id>
                <phase>package</phase>
                <goals>
                    <goal>single</goal>
                </goals>
            </execution>
        </executions>
    </plugin>
      ```

16. Verify project can build `mvn clean verify`
17. Execute the resulting jar file with some arguments
      ```
        java -jar target/maven-demo-1.0-SNAPSHOT-jar-with-dependencies.jar "Hello World!" 250
      ```
    to generate a QR Code for the text `"Hello World!"`, having a width of 250 pixels.

18. Check that QR Code is generated
