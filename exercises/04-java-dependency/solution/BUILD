java_binary(
    name = "app-binary",
    srcs = glob(["src/main/java/com/bmuschko/app/**/*.java"]),
    resources = glob(["src/main/resources/**/*"]),
    main_class = "com.bmuschko.app.Application",
    deps = [
        "@maven//:org_apache_commons_commons_configuration2",
        "@maven//:commons_beanutils_commons_beanutils",
    ],
)