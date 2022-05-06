# Exercise 8

In this exercise, you will write a genrule target named `zip-txt-files`. The implementation should use the `zip` command to package all text files found in the directory `text-files`. The produced ZIP should be named `all-text-files.zip`

Reference the documentation of the [genrule](https://bazel.build/reference/be/general#genrule) for more information.

1. Inspect the existing source code files in the `start` directory.
2. Write the genrule in the `BUILD`.
3. Execute the genrule target.
4. Inspect the contents of the produced ZIP file.
