genrule(
    name = "zip-txt-files",
    srcs = glob(["text-files/**"]),
    cmd = "zip -r $(OUTS) $(SRCS)",
    outs = [
        "all-text-files.zip",
    ],
)
