package(default_visibility = ["//visibility:public"])

java_library(
    name = "java-lib",
    srcs = glob(["src/main/java/*.java"])
)

java_test(
    name = "tests",
    srcs = glob(["src/test/java/*.java"]),
    test_class = "LibraryTest",
    deps = [
        ":java-lib",
        "@com_google_guava_guava//jar",
    ],
)

j2objc_library(
    name = "transpile_oc_source",
    deps = [
        ":java-lib"
    ],
    entry_classes = [
        "Library"
    ]
)

apple_binary(
    name = "run_oc",
    deps = [
        ":transpile_oc_source"
    ],
    platform_type = "ios"
) 

objc_library(
    name = "compile_oc",
    deps = [
        ":transpile_oc_source"
    ],
    hdrs = ["src/main/java/Library.h"]
)

load("@build_bazel_rules_apple//apple:ios.bzl", "ios_framework", "ios_static_framework")


# This does not share any header file in the bundle (somewhat expected)
ios_static_framework(
  name = "package_ocv1",
  families = ["iphone", "ipad"],  
  deps = [":transpile_oc_source"]
)

# This would be the ideal, but it does not work, bazel doesn't recognize any output header from transpile_oc_source
ios_static_framework(
  name = "package_ocv2",
  hdrs = [":transpile_oc_source"],
  families = ["iphone", "ipad"],  
  deps = [":transpile_oc_source"]
)

# This actually works after the second pass, since bazel finds the header that was created in the previous run pass, but its obviously not the way it should work
ios_static_framework(
  name = "package_ocv3",
  hdrs = glob(["bazel-out/**/_j2objc/**/*.h"]),
  families = ["iphone", "ipad"],  
  deps = [":transpile_oc_source"]
)