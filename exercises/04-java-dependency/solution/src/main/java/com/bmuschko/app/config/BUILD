java_library(
    name = "app-lib",
    srcs = glob(["*.java"]),
    visibility = ["//src/main/java/com/bmuschko/app:__pkg__"],
    deps = [
        "@maven//:org_apache_commons_commons_configuration2",
        "@maven//:commons_beanutils_commons_beanutils",
    ],
    runtime_deps = [
        "//src/main/resources:app-resources"
    ]
)