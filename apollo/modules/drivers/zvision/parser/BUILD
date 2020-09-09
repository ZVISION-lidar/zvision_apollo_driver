load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_binary(
    name = "libzvision_convert_component.so",
    linkshared = True,
    linkstatic = False,
    deps = [":zvision_convert_component_lib"],
)

cc_library(
    name = "zvision_convert_component_lib",
    srcs = ["zvision_convert_component.cc"],
    hdrs = ["zvision_convert_component.h"],
    copts = ['-DMODULE_NAME=\\"zvision\\"'],
    deps = [
        "//cyber",
        "//modules/drivers/zvision/parser:convert",
    ],
)

cc_library(
    name = "convert",
    srcs = [
        "convert.cc",
        "ml30_parser.cc",
        "ml30sa1_parser.cc",
        "mlx_parser.cc",
        "parser.cc",
    ],
    hdrs = [
        "convert.h",
        "parser.h",
    ],
    copts = ['-DMODULE_NAME=\\"zvision\\"'],
    deps = [
        "//cyber",
        "//modules/drivers/proto:sensor_proto",
        "//modules/drivers/zvision/proto:zvision_proto",
        "//modules/drivers/zvision/tools:tools",
        "@eigen",
    ],
)

cpplint()
