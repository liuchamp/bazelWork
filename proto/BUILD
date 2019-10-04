package(default_visibility = ["//visibility:public"])

load("@rules_proto//proto:defs.bzl", "proto_library")

proto_library(
    name = "thing_proto",
    srcs = [
        "greetertimer.proto",
        "helloworld.proto",
    ],
    deps = ["@com_google_protobuf//:any_proto"],
)

cc_proto_library(
    name = "thing_cc_proto",
    deps = [":thing_proto"],
)
