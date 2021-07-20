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
    deps = [
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-compiler-cranelift",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-compiler-singlepass",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-compiler-llvm",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-emscripten",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-engine",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-engine-universal",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-engine-dylib",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-engine-staticlib",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-middlewares",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-wasi",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer-types",
        "@proxy_wasm_cpp_host//bazel/cargo:enumset",
        "@proxy_wasm_cpp_host//bazel/cargo:cfg-if",
        "@proxy_wasm_cpp_host//bazel/cargo:lazy_static",
        "@proxy_wasm_cpp_host//bazel/cargo:libc",
        "@proxy_wasm_cpp_host//bazel/cargo:serde",
        "@proxy_wasm_cpp_host//bazel/cargo:thiserror",
        "@proxy_wasm_cpp_host//bazel/cargo:typetag",
        "@proxy_wasm_cpp_host//bazel/cargo:paste",
        "@proxy_wasm_cpp_host//bazel/cargo:wasmer",
    ],
)
