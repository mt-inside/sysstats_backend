workspace(name = "sysstats_backend")

# Define the repo of SkyLark rules
# Version 0.5.5
http_archive(
    name = "io_bazel_rules_go",
    strip_prefix = "rules_go-71cdb6fd5f887d215bdbe0e4d1eb137278b09c39",
    urls = [
        "http://mirror.bazel.build/github.com/bazelbuild/rules_go/archive/71cdb6fd5f887d215bdbe0e4d1eb137278b09c39.tar.gz",
        "https://github.com/bazelbuild/rules_go/archive/71cdb6fd5f887d215bdbe0e4d1eb137278b09c39.tar.gz",
    ],
)

load("@io_bazel_rules_go//go:def.bzl", "go_rules_dependencies", "go_register_toolchains")
go_rules_dependencies()
go_register_toolchains()

load("@io_bazel_rules_go//proto:def.bzl", "proto_register_toolchains")
proto_register_toolchains()

# Needed for tests
load("@io_bazel_rules_go//tests:bazel_tests.bzl", "test_environment")
test_environment()
