load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_library")
load("@io_bazel_rules_go//proto:def.bzl", "go_grpc_library")


# Just tells bzl where to find the protofiles. Used an input to future
# targets.
proto_library(
    name = "sysstats_proto",
    srcs = ["protos/sysstats.proto"],
    deps = [
        "@com_google_protobuf//:any_proto",
        "@com_google_protobuf//:empty_proto",
    ],
)

# is a type go_proto_library(), which seems to build proto serialise and
# deserialise stubs for Go

go_grpc_library(
    name = "sysstats_go_stubs",
    proto = ":sysstats_proto",
    # Has to match the go_package option in the protofile?
    importpath = "github.com/mt-inside/sysstats_backend/sysstats_proto",
    deps = [
        "@com_github_golang_protobuf//ptypes/any:go_default_library",
        "@com_github_golang_protobuf//ptypes/empty:go_default_library",
    ],
)

go_binary(
    name = "sysstats_backend",
    srcs = ["main.go"],
    importpath = "github.com/mt-inside/sysstats_backend/main",
    deps = [
        ":sysstats_go_stubs",
        # Necessary here?
        "@com_github_golang_protobuf//ptypes/any:go_default_library",
        "@com_github_golang_protobuf//ptypes/empty:go_default_library",
        # GRPC System libraries?
        "@org_golang_google_grpc//:go_default_library",
        "@org_golang_x_net//context:go_default_library",
    ],
)
