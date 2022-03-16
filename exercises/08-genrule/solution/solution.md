# Solution

Navigate to the `start` directory.

```
$ cd start
```

Add the genrule to the `BUILD` file. Point the input sources to all files in the directory `text-files`. The outputs should be directed to the file `all-text-files.zip`. The `zip` command takes care of packaging the files. You can reference the values of the `srcs` and `outs` attributes using `$(SRCS)` and `$(OUTS)`.

```
genrule(
  name = "zip-txt-files",
  srcs = glob(["text-files/**"]),
  cmd = "zip -r $(OUTS) $(SRCS)",
  outs = [
    "all-text-files.zip",
  ],
)
```

When you run the target `zip-txt-files` all files found in the directory `text-files` will be zipped up.

```
$ bazel build //:zip-txt-files

INFO: Analyzed target //:zip-txt-files (5 packages loaded, 10 targets configured).
INFO: Found 1 target...
INFO: From Executing genrule //:zip-txt-files:
  adding: text-files/a.txt (deflated 38%)
  adding: text-files/b.txt (deflated 29%)
  adding: text-files/c.txt (deflated 12%)
Target //:zip-txt-files up-to-date:
  bazel-bin/all-text-files.zip
INFO: Elapsed time: 0.775s, Critical Path: 0.04s
INFO: 2 processes: 1 internal, 1 darwin-sandbox.
INFO: Build completed successfully, 2 total actions
...
```

The ZIP file should contain three files.

```
$ unzip -l bazel-bin/all-text-files.zip
Archive:  bazel-bin/all-text-files.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
      231  03-15-2022 20:05   text-files/a.txt
      186  03-15-2022 20:05   text-files/b.txt
       78  03-15-2022 20:06   text-files/c.txt
---------                     -------
      495                     3 files
```