load("@rules_rust//rust:defs.bzl", "rust_binary")
load("@crate_index//:defs.bzl", "all_crate_deps")

package(default_visibility = ["//visibility:public"])

rust_binary(
    name = "bin",
    srcs = [
        "src/main.rs",
    ],
    edition = "2021",
    deps = all_crate_deps(
        normal = True,
    ),
)
