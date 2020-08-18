load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_binary(
    name = "libzvision_driver_component.so",
    linkopts = ["-shared"],
    linkstatic = False,
    deps = [":zvision_driver_component_lib"],
)

cc_library(
    name = "zvision_driver_component_lib",
    srcs = ["zvision_driver_component.cc"],
    hdrs = ["zvision_driver_component.h"],
    copts = ['-DMODULE_NAME=\\"zvision\\"'],
    deps = [
        "//cyber",
        "//modules/common/util:message_util",
        "//modules/drivers/zvision/driver",
    ],
)

cc_library(
    name = "driver",
    srcs = [
        "zvision_driver.cc",
        "socket_input.cc",
    ],
    hdrs = [
        "zvision_driver.h",
        "input.h",
        "socket_input.h",
    ],
    copts = ['-DMODULE_NAME=\\"zvision\\"'],
    deps = [
        "//cyber",
        "//modules/common/util",
        "//modules/drivers/zvision/proto:zvision_proto",
    ],
)

cpplint()
