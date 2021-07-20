load("@rules_cc//cc:defs.bzl", "cc_library")
load("@rules_rust//rust:rust.bzl", "rust_library")

licenses(["notice"])  # Apache 2

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "helpers_lib",
    srcs = [
        "lib/vm/src/trap/handlers.c",
    ],
    visibility = ["//visibility:private"],
)

rust_library(
    name = "rust_c_api",
    srcs = glob(["lib/c-api/src/**/*.rs"]),
    crate_features = [],
    crate_root = "lib/c-api/src/lib.rs",
    crate_type = "staticlib",
    edition = "2018",
    proc_macro_deps = [
        "@proxy_wasm_cpp_host//bazel/cargo:paste",
    ],
    deps = [
        ":helpers_lib",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer_compiler_llvm",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer_engine",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer_engine_universal",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer_types",
        "@proxy_wasm_cpp_host//bazel/cargo:enumset",
        "@proxy_wasm_cpp_host//bazel/cargo:cfg_if",
        "@proxy_wasm_cpp_host//bazel/cargo:lazy_static",
        "@proxy_wasm_cpp_host//bazel/cargo:libc",
        "@proxy_wasm_cpp_host//bazel/cargo:serde",
        "@proxy_wasm_cpp_host//bazel/cargo:thiserror",
        "@proxy_wasm_cpp_host//bazel/cargo:typetag",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer",
    ],
)
