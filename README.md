## Yet another Debian Docker image for Tomcat, Java with unlimited JCE patch applied

[![Build Status](https://travis-ci.org/davidcaste/docker-debian-tomcat.svg?branch=master)](https://travis-ci.org/davidcaste/docker-debian-tomcat)

[![](https://badge.imagelayers.io/davidcaste/debian-tomcat:latest.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:latest)

Basic [Docker](https://www.docker.com/) image to run [Tomcat](https://tomcat.apache.org/) and [Java](https://www.java.com/) applications, based on [Debian](http://www.debian.org/) Jessie. This image is patched with Java Cryptographic Extension (JCE) Unlimited Strength Jurisdiction Policy Files.

It also includes Bash, since many Java applications like to have convoluted Bash start-up scripts.

Extends [`davidcaste/debian-oracle-java`](https://hub.docker.com/r/davidcaste/debian-oracle-java/).


### Versions

**Tomcat 8 Version**: `8.0.33`  
**Tomcat 7 Version**: `7.0.69`  
**JRE8/JDK8 Version**: `8u92-b14`  
**JRE7/JDK7 Version**: `7u80-b15`

### Tags

| Tomcat version | Java version      | tags                                 | Size                                                                                                                                              |
|:---------------|:------------------|:-------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| Tomcat 8       | Oracle Java 8 JRE | `latest` / `tomcat8` / `jre8tomcat8` | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jre8tomcat8.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jre8tomcat8) |
| Tomcat 8       | Oracle Java 8 JDK | `jdk8tomcat8`                        | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jdk8tomcat8.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jdk8tomcat8) |
| Tomcat 8       | Oracle Java 7 JRE | `jre7tomcat8`                        | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jre7tomcat8.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jre7tomcat8) |
| Tomcat 8       | Oracle Java 7 JDK | `jdk7tomcat8`                        | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jdk7tomcat8.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jdk7tomcat8) |
| Tomcat 7       | Oracle Java 8 JRE | `tomcat7` / `jre8tomcat7`            | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jre8tomcat7.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jre8tomcat7) |
| Tomcat 7       | Oracle Java 8 JDK | `jdk8tomcat7`                        | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jdk8tomcat7.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jdk8tomcat7) |
| Tomcat 7       | Oracle Java 7 JRE | `jre7tomcat7`                        | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jre7tomcat7.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jre7tomcat7) |
| Tomcat 7       | Oracle Java 7 JDK | `jdk7tomcat7`                        | [![](https://badge.imagelayers.io/davidcaste/debian-tomcat:jdk7tomcat7.svg)](https://imagelayers.io/?images=davidcaste/debian-tomcat:jdk7tomcat7) |


### Usage

Some indications:

* Tomcat installation directory is `/opt/tomcat` (`$TOMCAT_HOME`/`$CATALINA_HOME`). Executable scripts are found in directory `$TOMCAT_HOME/bin` and the application base (*appBase*) directory is `$TOMCAT_HOME/webapps`.
* The path of file `catalina.out` is managed by the variable `$CATALINA_OUT`, and its value by default is `/dev/null` (disabled).
* Apache logs are written into directory `/logs/`.

There are two ways to use this image:

1. Use it as base image for other images. For example:

  ```
  FROM davidcaste/debian-tomcat:tomcat8
  ```

1. Use the image directly, and copy the `.war` files directly into the *appBase* directory. For example:

  ```
  docker run -it --rm davidcaste/debian-tomcat /opt/tomcat/bin/catalina.sh run
  docker cp ./sample.war tomcat-ci:/opt/tomcat/webapps/sample.war
  ```
