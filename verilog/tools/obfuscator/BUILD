"""Tool for obfuscating verilog
"""

licenses(["notice"])

cc_binary(
    name = "verible-verilog-obfuscate",
    srcs = ["verilog_obfuscate.cc"],
    visibility = ["//visibility:public"],
    deps = [
        "//common/strings:obfuscator",
        "//common/util:file_util",
        "//common/util:init_command_line",
        "//verilog/analysis:verilog_analyzer",
        "//verilog/analysis:extractors",
        "//verilog/transform:obfuscate",
        "@com_google_absl//absl/flags:flag",
        "@com_google_absl//absl/strings",
    ],
)

# For a limited time, we provide the old name to be compatible with the
# old installation. At some point, this script will print a deprecation warning
# and be removed entirely later.
filegroup(
    name = "verilog_obfuscate-deprecated",
    srcs = [
        "verilog_obfuscate",
        ":verible-verilog-obfuscate",
    ],
    visibility = ["//visibility:public"],
)

sh_test(
    name = "obfuscate_test",
    size = "small",
    srcs = ["obfuscate_test.sh"],
    args = [
        "$(location :verible-verilog-obfuscate)",
        "$(location //verilog/tools/diff:verible-verilog-diff)",
    ],
    data = [
        ":verible-verilog-obfuscate",
        "//verilog/tools/diff:verible-verilog-diff",
    ],
)
