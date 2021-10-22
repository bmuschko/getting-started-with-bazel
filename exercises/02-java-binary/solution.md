# Solution

Navigate to the `start` directory.

```
$ cd start
```

Create the `WORKSPACE` file in the root directory. There's no need to add content to the file.

```
$ touch WORKSPACE
```

Create the `BUILD` file in the root directory. Assign all Java source code files to the `srcs` attribute. Assign the resource files to the `resources` attribute.

```
java_binary(
    name = "app-binary",
    srcs = glob(["src/main/java/com/bmuschko/app/**/*.java"]),
    resources = glob(["src/main/resources/**/*"]),
    main_class = "com.bmuschko.app.Application",
)
```

Running the application will print two different properties that have been processed from the `application.properties` file.

```
$ bazel run //:app-binary
Starting local Bazel server and connecting to it...
INFO: Analyzed target //:app-binary (24 packages loaded, 668 targets configured).
INFO: Found 1 target...
Target //:app-binary up-to-date:
  bazel-bin/app-binary.jar
  bazel-bin/app-binary
INFO: Elapsed time: 5.674s, Critical Path: 0.31s
INFO: 1 process: 1 internal.
INFO: Build completed successfully, 1 total action
INFO: Build completed successfully, 1 total action
profile: production
version: 1.0.0
```