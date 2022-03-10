# Exercise 4

In this exercise, you will declare package dependencies for a Java-based project. We'll want to model the directories `src/main/java/com/bmuschko/app`, `src/main/java/com/bmuschko/app/config`, and `src/main/resources` as fine-grained Bazel packages with dependencies to each other as needed.

The following image shows the high-level architecture.

![java-binary](imgs/java-external-dependency.png)

Reference the documentation of the [java_binary rule](https://docs.bazel.build/versions/main/be/java.html#java_binary) and [java_library rule](https://docs.bazel.build/versions/main/be/java.html#java_library) for more information.

1. Inspect the existing source code files in the `start` directory.
2. Define a `WORKSPACE` file in the root directory of `start`. Leave the file empty for now.
3. Define a `BUILD` file for the individual directories mentioned above. The package `src/main/java/com/bmuschko/app` should use the java_binary rule. The package `src/main/java/com/bmuschko/app/config` and `src/main/resources` should use the java_library rule. Define package dependencies and visibility as you see fit.
4. Run the main class `com.bmuschko.app.Application` of the compiled program. Ensure that the error message indicates that the external dependency cannot be resolved.