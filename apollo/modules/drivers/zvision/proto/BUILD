## Auto generated by `proto_build_generator.py`
load("//tools:cpplint.bzl", "cpplint")
package(default_visibility = ["//visibility:public"])

cc_library(
    name = "zvision_proto",
    deps = [
        ":sensor_zvision_proto",
    ],
)

cc_proto_library(
    name = "sensor_zvision_proto",
    deps = [
        ":zvision_proto_lib",
    ],
)

proto_library(
    name = "zvision_proto_lib",
    srcs = [
        "config.proto",
        "zvision.proto",
    ],
    deps = [
        "//modules/common/proto:header_proto_lib",
    ],
)


