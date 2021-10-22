# Solution

Navigate to the `start` directory.

```
$ cd start
```

Create the `WORKSPACE` file in the root directory. There's no need to add content to the file.

```
$ touch WORKSPACE
```

The `src/main/java/com/bmuschko/app/BUILD` file looks as follows. It needs to have a package dependency on the java library created by the `config` package.

```
java_binary(
    name = "app-binary",
    srcs = ["Application.java"],
    main_class = "com.bmuschko.app.Application",
    deps = [
        "//src/main/java/com/bmuschko/app/config:app-lib"
    ]
)
```

The `src/main/java/com/bmuschko/app/config/BUILD` file looks as follows. It needs to have a dependency on the java library created by the `resources` package. Notice that we only need the resources at runtime and not compile-time. To be consumed, this package needs to change its visibility.

```
java_library(
    name = "app-lib",
    srcs = glob(["*.java"]),
    visibility = ["//src/main/java/com/bmuschko/app:__pkg__"],
    runtime_deps = [
        "//src/main/resources:app-resources"
    ]
)
```

The `src/main/resources/BUILD` file looks as follows. It needs to bundle the property files and make itself consumable from the `config` package.

```
java_library(
    name = "app-resources",
    srcs = glob(["*.properties"]),
    visibility = ["//src/main/java/com/bmuschko/app/config:__pkg__"]
)
```