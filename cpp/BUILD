cc_binary(
    name = "route_guide_server",
    srcs = [
        "helper.cc",
        "helper.h",
        "server.cc",
    ],
    data = ["route_guide_db.json"],
    defines = ["BAZEL_BUILD"],
    deps = [
        "//:grpc++",
        "//proto:thing_proto",
    ],
)
