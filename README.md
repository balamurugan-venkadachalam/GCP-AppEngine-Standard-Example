Standard Enviroment
============================
 App Engine uses Jetty Web Server 9 with servlet 3.1 along with accompanying technologies such as JSP, JSF, Struts required workaround.
 
 

## appengine-standard-archetype


This is a generated App Engine Standard Java application from the appengine-standard-archetype archetype.

See the [Google App Engine standard environment documentation][ae-docs] for more
detailed instructions.

[ae-docs]: https://cloud.google.com/appengine/docs/java/


* [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
* [Maven](https://maven.apache.org/download.cgi) (at least 3.5)
* [Google Cloud SDK](https://cloud.google.com/sdk/) (aka gcloud)

## Setup

    gcloud init
    gcloud auth application-default login

## Maven
### Running locally

    mvn appengine:devserver

### Deploying

    mvn appengine:update

## Testing

    mvn verify

As you add / modify the source code (`src/main/java/...`) it's very useful to add
[unit testing](https://cloud.google.com/appengine/docs/java/tools/localunittesting)
to (`src/main/test/...`).  The following resources are quite useful:

* [Junit4](http://junit.org/junit4/)
* [Mockito](http://mockito.org/)
* [Truth](http://google.github.io/truth/)

## Updating to latest Artifacts

An easy way to keep your projects up to date is to use the maven [Versions plugin][versions-plugin].

    mvn versions:display-plugin-updates
    mvn versions:display-dependency-updates
    mvn versions:use-latest-versions

Note - Be careful when changing `javax.servlet` as App Engine Standard uses 3.1 for Java 8, and 2.5
for Java 7.

Our usual process is to test, update the versions, then test again before committing back.

[plugin]: http://www.mojohaus.org/versions-maven-plugin/

## Scaling
App Engine supports the following scaling types, which controls how and when instances are created:
* Auto Scaling
* Manual Scaling
* Basic Scaling

https://cloud.google.com/appengine/docs/standard
https://cloud.google.com/appengine/docs/standard/java/how-instances-are-managed#scaling_dynamic_instances

## URL Pattern
```
https://VERSION_ID-dot-SERVICE_ID-dot-PROJECT_ID.REGION_ID.r.appspot.com
```
For example
```
https://20200419t154727-dot-test-dot-first-gcp-project.uc.r.appspot.com
```
more details please refer [here](https://cloud.google.com/appengine/docs/standard/java/an-overview-of-app-engine#versions_and_instances)  

## Instance Class
| Instance Class | Memory Limit | CPU Limit | Supported Scaling Types |
| -------------- | ------------ | --------- | ----------------------- |
| F1 (default)	| 256 MB | 600 MHz	| automatic
|F2	|512 MB	|1.2 GHz	|automatic
|F4	|1024 MB	|2.4 GHz	|automatic
|F4_1G	|2048 MB	|2.4 GHz	|automatic
|B1	|256 MB	|600 MHz	|manual, basic
|B2 (default)	|512 MB	|1.2 GHz	|manual, basic
|B4	1024 |MB	|2.4 GHz	|manual, basic
|B4_1G	|2048 MB	|2.4 GHz	|manual, basic
|B8|	2048 MB	|4.8 GHz	|manual, basic

Please refer [here](https://cloud.google.com/appengine/docs/standard)

## Spring Boot Application

Because App engine standard is running in a Jetty Web Server, the default configuration for a Spring Boot application will not work. 
This causes several conflicts because Spring Boot uses an embedded Tomcat Web Server. More information about the configuration of a Spring Boot application for the standard environment can be found [here](https://github.com/GoogleCloudPlatform/getting-started-java/tree/master/appengine-standard-java8/springboot-appengine-standard).

## Debug
GCP console -> App Engine -> Dashboad -> select service -> Debug -> select load appropriate code from github or gcp repo  

 - [x] https://cloud.google.com/debugger/docs/source-options

 - [x] https://cloud.google.com/eclipse/docs/running-and-debugging


 ## Reference 
 - [x] https://cloud.google.com/appengine/docs/standard/java/how-to
 - [x] https://cloud.google.com/appengine/docs/standard/java/config/appref
 - [x] https://cloud.google.com/appengine/docs/standard/java/config/appref#scaling_elements_automatic_scaling
 - [x] https://cloud.google.com/appengine/docs/standard/java/reference/dispatch-yaml
 - [x] https://github.com/GoogleCloudPlatform/getting-started-java/tree/master/appengine-standard-java8/springboot-appengine-standard
 - [x] https://www.vogella.com/tutorials/GoogleAppEngineJava/article.html
 - [x] https://dzone.com/articles/deploy-spring-boot-app-to-gcp-app-engine
 - [x] https://codelabs.developers.google.com/codelabs/cloud-app-engine-springboot/index.html?index=..%2F..index#0
 