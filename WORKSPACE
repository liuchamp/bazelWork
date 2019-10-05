# File //:WORKSPACE
workspace(name = "org_pubref_grpc_greetertimer")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_proto",
    sha256 = "602e7161d9195e50246177e7c55b2f39950a9cf7366f74ed5f22fd45750cd208",
    strip_prefix = "rules_proto-97d8af4dc474595af3900dd85cb3a29ad28cc313",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_proto/archive/97d8af4dc474595af3900dd85cb3a29ad28cc313.tar.gz",
        "https://github.com/bazelbuild/rules_proto/archive/97d8af4dc474595af3900dd85cb3a29ad28cc313.tar.gz",
    ],
)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

http_archive(
    name = "com_github_grpc_grpc",
    strip_prefix = "grpc-1.24.1",
    urls = [
        "https://github.com/grpc/grpc/archive/v1.24.1.zip",
    ],
)

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps", "grpc_test_only_deps")

grpc_deps()

grpc_test_only_deps()

register_execution_platforms(
    "//third_party/toolchains:local",
    "//third_party/toolchains:local_large",
    "//third_party/toolchains:rbe_windows",
)

register_toolchains(
    "//third_party/toolchains/bazel_0.26.0_rbe_windows:cc-toolchain-x64_windows",
)

load("@bazel_toolchains//rules:rbe_repo.bzl", "rbe_autoconfig")

# Create toolchain configuration for remote execution.
rbe_autoconfig(
    name = "rbe_default",
)

load("@bazel_toolchains//rules:environments.bzl", "clang_env")
load("@bazel_skylib//lib:dicts.bzl", "dicts")

# Create msan toolchain configuration for remote execution.
rbe_autoconfig(
    name = "rbe_msan",
    env = dicts.add(
        clang_env(),
        {
            "BAZEL_LINKOPTS": "-lc++:-lc++abi:-lm",
        },
    ),
)

load("@upb//bazel:workspace_deps.bzl", "upb_deps")

upb_deps()
