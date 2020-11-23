---
title: Build With Maven
nav_order: 19
has_children: true
---

# Lesson 19: Build With Maven

## Goals

- Build jar
- Build executive jar

## Maven Build Lifecycle

See [**Maven Build Lifecycle**](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)

The default lifecycle comprises of the following phases:

- `validate` - validate the project is correct and all necessary information is available
- `compile`- compile the source code of the project
- `test` - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
- `package` - take the compiled code and package it in its distributable format, such as a JAR.
- `verify` - run any checks on results of integration tests to ensure quality criteria are met
- `install` - install the package into the local repository, for use as a dependency in other projects locally
- `deploy` - done in the build environment, copies the final package to the remote repository for sharing with other developers and projects.

These lifecycle phases (plus the other lifecycle phases not shown here) are executed sequentially to complete the default
lifecycle. Given the lifecycle phases above, this means that when the default lifecycle is used, Maven will first 
validate the project, then will try to compile the sources, run those against the tests, package the binaries (e.g. jar),
run integration tests against that package, verify the integration tests, install the verified package to the local repository, 
then deploy the installed package to a remote repository.

In most of the cases you would only need to execute the following:

```
mvn clean verify
```

- `clean` - to  delete any previous build so that a fresh build can be done
- `verify` - to execute the build lifecycle from `validate` to `verify`

## Install Maven
For Mac users, if you have `brew` installed you can simply execute `brew install maven` to have maven on your machine.

Otherwise, follow these instructions

1. [Downloading Apache Maven 3.6.3](https://maven.apache.org/download.cgi?Preferred=https%3A%2F%2Fapache.claz.org%2F)
   - Here, you will download a compressed file that contains the maven distribution.
2. [Extract the downloaded archive](https://maven.apache.org/install.html) 
   - It is important that you extract the archive downloaded into a directory that is not easily deleted.
   - Mac/Linux `/opt/apache-maven-3.6.3` 
   - Windows`C:\Program Files\apache-maven-3.6.3` 
3. Add the `bin` directory of the extracted directory `apache-maven-3.6.3` to the `PATH` environment variable
   - Mac/Linux]
     - [See how to set an environment variable](https://stackoverflow.com/a/31546962)
       ```
       export PATH=/opt/apache-maven-3.6.3/bin:$PATH
       ```
     - Start a new terminal and verify the `PATH` with `echo PATH`
   - Windows 
     - [See how to set an environment variable](https://maven.apache.org/install.html#windows-tips)
     - Append the directory to the existing `PATH`
     - Start a new terminal and verify the `PATH` with `echo %PATH%`
4. Set or verify the `JAVA_HOME` environment variable using the same method above
5. Open a new terminal and run `mvn -v` to verify the installation.


## Maven Project: An Application that generates QR Code

- Create a new maven project on Intellij.
- Verify project can build `mvn clean verify`
- [Set Java Version For New Project](https://maven.apache.org/plugins/maven-compiler-plugin/examples/set-compiler-source-and-target.html)
- Create a package (`com.redi.maven`) 
- Create an `Application` class with a `main` method that prints `Hello world!`.
- Set the main class for the jar plugin
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
- Verify project can build `mvn clean verify`
- Execute the resulting jar file `java -jar target/maven-demo-1.0-SNAPSHOT.jar`
- Add dependency for [ZXing](https://zxing.github.io/zxing/project-info.html) which will be used to generate QR Codes
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
- Add code to generate QR Code
  ```java
      final String text = args.length > 0 ? args[0] : "dummy";
      final int size = args.length > 1 ? Integer.parseInt(args[1]) : 100;
      final BitMatrix result = new MultiFormatWriter().encode(text, BarcodeFormat.QR_CODE, size, size, null);
      final BufferedImage image = MatrixToImageWriter.toBufferedImage(result);
      final File outputfile = new File(text + ".jpg");
      ImageIO.write(image, "jpg", outputfile);
  ```
- Execute using IntelliJ and inspect the generated QR Code.
- Verify project can build `mvn clean verify`
- Execute the resulting jar file with some arguments 
  ```
    java -jar target/maven-demo-1.0-SNAPSHOT.jar "Hello World!" 250
  ```
  to generate a QR Code for the text `"Hello World!"`, having a width of 250 pixels.
- Exception because not all classes and libraries are included in the jar file
  ```
  Error: Unable to initialize main class com.redi.maven.Application
  Caused by: java.lang.NoClassDefFoundError: com/google/zxing/WriterException
  ```
- Building an executable jar with all dependencies. This is only needed if you want to ship an application that needs to be executed standalone.
  **This is not need for creating and deploying libraries for use.**
  Add the maven assembly plugin to enable packaging jar with dependencies
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
- Verify project can build `mvn clean verify`
- Execute the resulting jar file with some arguments 
  ```
    java -jar target/maven-demo-1.0-SNAPSHOT-jar-with-dependencies.jar "Hello World!" 250
  ```
  to generate a QR Code for the text `"Hello World!"`, having a width of 250 pixels.
- Check that QR Code is generated
