java_library(
    name = "app-config-lib",
    srcs = glob(["*.java"]),
    deps = [
        "@maven//:org_apache_commons_commons_configuration2"
    ],
    runtime_deps = [
        "@maven//:commons_beanutils_commons_beanutils"
    ]
)

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
