# Exercise 7

In this exercise, you will publish Java library produced by the package `src/main/java/com/bmuschko/app/config` to the Maven Local repository at `~/.m2/repository`. The generated POM file should contain the dependencies required for the package.

Reference the documentation of the [java_export rule](https://github.com/bazelbuild/rules_jvm_external#publishing-to-external-repositories) for more information.

1. Inspect the existing source code files in the `start` directory.
2. Load the java_export rule in the file `src/main/java/com/bmuschko/app/config/BUILD`.
3. Define a java_export target with the name `app-config-lib-export`. The GAV for the published artifacts should be `com.bmuschko.app:config:1.0.0`. The POM should declare the transitive dependencies `org.apache.commons:commons-configuration2:2.7` and `commons-beanutils:commons-beanutils:1.9.2`.
4. Execute the command for publishing the artifacts.
5. Inspect the generated files. Does the POM contain the right dependency declarations?
