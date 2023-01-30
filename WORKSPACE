workspace(name = "test_jwt")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# RUST #########################################################################

http_archive(
    name = "rules_rust",
    sha256 = "d125fb75432dc3b20e9b5a19347b45ec607fabe75f98c6c4ba9badaab9c193ce",
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/0.17.0/rules_rust-v0.17.0.tar.gz"],
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")

rules_rust_dependencies()

rust_register_toolchains(
    edition = "2021",
    extra_target_triples = [
        "aarch64-apple-ios",
    ],
    # rustup default nightly-2023-01-26
    rustfmt_version = "nightly/2023-01-26",
    versions = ["nightly/2023-01-26"],
)

load("@rules_rust//crate_universe:defs.bzl", "crates_repository", "splicing_config")

crates_repository(
    name = "crate_index",
    cargo_lockfile = "//:Cargo.Bazel.lock",
    isolated = False,  # WAYYYYYYY faster splicing
    lockfile = "//:cargo-bazel-lock.json",
    manifests = [
        "//:Cargo.toml",
    ],
    rust_version = "nightly/2023-01-26",
    splicing_config = splicing_config(
        resolver_version = "2",
    ),
)

load(
    "@crate_index//:defs.bzl",
    crate_index_repositories = "crate_repositories",
)

crate_index_repositories()
