# Application - TWOCALIZE

* *Author* : [Christophe BEDU]
* *Technologies* : Java EE 6 (JPA 2.0, CDI 1.0, Bean Validation 1.0, EJB Lite 3.1, JSF 2.0, JAX-RS 1.1)
* *Application Servers : GlassFish 3.x
* *Summary* : Twocalize

[Download the code from GitHub](https://github.com/twocalize)

## Purpose of this application

Twocalize !!!

## Component diagram

## Glassfish 3.1.2

[Glassfish](http://glassfish.java.net) is the [Java EE 6](http://jcp.org/en/jsr/detail?id=316) reference implementation.

## Compile and package

Being Maven centric, you can compile and package it with `mvn clean compile`, `mvn clean package` or `mvn clean install`. The `package` and `install` phase will automatically trigger the unit tests. Once you have your war file, you can deploy it.

GlassFish is the default deployment application server, so you don't need to use any Maven profile. But if you wanted you could do `mvn -Pglassifh-embedded clean install`.

### Test with Glassfish embedded

Launching tests under [Glassfish](http://glassfish.java.net/public/downloadsindex.html) is straight forward. You only have to lauch :

    mvn clean install -Pglassfish-embedded

Galssfish will launch during the build and tests will be executed in it.

### Deploy in Glassfish

This sample has been tested with GlassFish 3.1.2 in several modes :

* GlassFish runtime : [download GlassFish](http://glassfish.java.net/public/downloadsindex.html), install it, start GlassFish (typing `asadmin start-`domain) and once the application is packaged deploy it (using the admin console or the command line `asadmin deploy target/applicationTwocalize.war`)
* GlassFish embedded : use the [GlassFish Maven Plugin](http://maven-glassfish-plugin.java.net/) by running `mvn clean package embedded-glassfish:run` (you might have to increase Perm Gen space with `MAVEN_OPTS` set to `-XX:MaxPermSize=128m`)

## Third Party Tools & Frameworks

### JRebel

[JRebel](http://zeroturnaround.com/software/jrebel/) is a JVM-plugin that makes it possible for Java developers to instantly see any code change made to an app without redeploying. It is very useful when you develop in a managed environment like application servers. If you need/want to use JRebel, just follow the [manual](http://zeroturnaround.com/software/jrebel/documentation/). To generate a rebel.xml file just do  `mvn jrebel:generate`

### Sonar

[Sonar](http://www.sonarsource.org/) provides services for continuous inspection of code quality. I use it to have some metrics on the Yaps Petstore (and produce, hopefully, not too ugly code with good code coverage). You can also use it to get some metrics. [Download](http://www.sonarsource.org/downloads/), [install](http://docs.codehaus.org/display/SONAR/Installing+Sonar) and run Sonar with `mvn -Pjacoco,glassfish3 install sonar:sonar` (or `mvn -Pjacoco,jboss7 install sonar:sonar` to run on JBoss 7). For integration testing we need to use [JaCoCo](http://www.eclemma.org/jacoco/). To view the code coverage of integartion tests, make sure you add the "Integration test coverage" widget to your Sonar dashboard (you need admin priviliges).

