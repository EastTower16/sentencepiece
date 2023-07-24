load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")



# Bazel Skylib.
http_archive(
    name = "bazel_skylib",  # 2022-11-16T18:29:32Z
    sha256 = "a22290c26d29d3ecca286466f7f295ac6cbe32c0a9da3a91176a90e0725e3649",
    strip_prefix = "bazel-skylib-5bfcb1a684550626ce138fe0fe8f5f702b3764c3",
    urls = ["https://github.com/bazelbuild/bazel-skylib/archive/5bfcb1a684550626ce138fe0fe8f5f702b3764c3.zip"],
)


rules_python_version = "740825b7f74930c62f44af95c9a4c1bd428d2c53" # Latest @ 2021-06-23

http_archive(
    name = "rules_python",
    # Bazel will print the proper value to add here during the first build.
    # sha256 = "FIXME",
    strip_prefix = "rules_python-{}".format(rules_python_version),
    url = "https://github.com/bazelbuild/rules_python/archive/{}.zip".format(rules_python_version),
)

http_archive(
    name = "com_google_protobuf",
    # sha256 = "f1748989842b46fa208b2a6e4e2785133cfcc3e4d43c17fecb023733f0f5443f",
    strip_prefix = "protobuf-3.14.0",
    urls = [
        "https://github.com/protocolbuffers/protobuf/archive/v3.14.0.tar.gz",
    ],
)


http_archive(
    name = "com_google_protobuf_cc",
    # sha256 = "f1748989842b46fa208b2a6e4e2785133cfcc3e4d43c17fecb023733f0f5443f",
    strip_prefix = "protobuf-3.14.0",
    urls = [
        "https://github.com/protocolbuffers/protobuf/archive/v3.14.0.tar.gz",
    ],
)


bind(
    name = "protocol_compiler",
    actual = "@com_google_protobuf//:protoc",
)

bind(
    name = "protobuf_headers",
    actual = "@com_google_protobuf//:protobuf_headers",
)


http_archive(
    name="com_google_absl",
    sha256 = "ea1d31db00eb37e607bfda17ffac09064670ddf05da067944c4766f517876390",
    strip_prefix = "abseil-cpp-c2435f8342c2d0ed8101cb43adfd605fdc52dca2",
    urls = ["https://github.com/abseil/abseil-cpp/archive/c2435f8342c2d0ed8101cb43adfd605fdc52dca2.zip"],
)

http_archive(
    name = "zlib",
    build_file = "//:zlib.BUILD",
    sha256 = "36658cb768a54c1d4dec43c3116c27ed893e88b02ecfcb44f2166f9c0b7f2a0d",
    strip_prefix = "zlib-1.2.8",
    urls = [
        # "http://bazel-mirror.storage.googleapis.com/zlib.net/zlib-1.2.8.tar.gz",
        "http://zlib.net/fossils/zlib-1.2.8.tar.gz",
    ],
)


