# Solution

Navigate to the `start` directory.

```
$ cd start
```

Add the `java_export` rule to the `src/main/java/com/bmuschko/app/config/BUILD` file as follows.

```
load("@rules_jvm_external//:defs.bzl", "java_export")

java_export(
    name = "app-config-lib-export",
    maven_coordinates = "com.bmuschko.app:config:1.0.0",
    srcs = glob(["*.java"]),
    deps = [
        "@maven//:org_apache_commons_commons_configuration2"
    ],
    runtime_deps = [
        "@maven//:commons_beanutils_commons_beanutils"
    ]
)
```

Publish the artifact and its POM to the standard Maven Local directory.

```
$ bazelisk run --define "maven_repo=file://$HOME/.m2/repository" //src/main/java/com/bmuschko/app/config:app-config-lib-export.publish
INFO: Build option --define has changed, discarding analysis cache.
INFO: Analyzed target //src/main/java/com/bmuschko/app/config:app-config-lib-export.publish (1 packages loaded, 900 targets configured).
INFO: Found 1 target...
Target //src/main/java/com/bmuschko/app/config:app-config-lib-export.publish up-to-date:
  bazel-bin/src/main/java/com/bmuschko/app/config/app-config-lib-export.publish-publisher
INFO: Elapsed time: 0.216s, Critical Path: 0.01s
INFO: 2 processes: 2 internal.
INFO: Build completed successfully, 2 total actions
INFO: Build completed successfully, 2 total actions
Uploading com.bmuschko.app:config:1.0.0 to file:///Users/bmuschko/.m2/repository
...
```

The published directory contains the following files:

```
$ tree /Users/bmuschko/.m2/repository/com/bmuschko/app/config/1.0.0
/Users/bmuschko/.m2/repository/com/bmuschko/app/config/1.0.0
├── config-1.0.0-javadoc.jar
├── config-1.0.0-javadoc.jar.md5
├── config-1.0.0-javadoc.jar.sha1
├── config-1.0.0-sources.jar
├── config-1.0.0-sources.jar.md5
├── config-1.0.0-sources.jar.sha1
├── config-1.0.0.jar
├── config-1.0.0.jar.md5
├── config-1.0.0.jar.sha1
├── config-1.0.0.pom
├── config-1.0.0.pom.md5
└── config-1.0.0.pom.sha1

0 directories, 12 files
```

The generated POM file has the following content:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd" xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.bmuschko.app</groupId>
    <artifactId>config</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <dependency>
            <groupId>commons-beanutils</groupId>
            <artifactId>commons-beanutils</artifactId>
            <version>1.9.2</version>
        </dependency>
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-configuration2</artifactId>
            <version>2.7</version>
        </dependency>
    </dependencies>
</project>
```
