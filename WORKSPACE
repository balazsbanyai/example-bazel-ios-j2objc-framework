maven_jar(
    name = "com_google_guava_guava",
    artifact = "com.google.guava:guava:18.0",
    server = "maven_uk_server",
)

maven_server(
    name = "maven_uk_server",
    url = "http://uk.maven.org/maven2",
)

http_archive(
    name = "bazel_j2objc",
    url = "https://github.com/google/j2objc/releases/download/2.0.3/j2objc-2.0.3.zip",
    # Computed using "shasum -a 256 j2objc-2.0.3.zip"
    sha256 = "a36bac432d0dbd8c98249e484b2b69dd5720afa4abb58711a3c3def1c0bfa21d",
    strip_prefix = "j2objc-2.0.3",
)

git_repository(
    name = "bazel_skylib",
    remote = "https://github.com/bazelbuild/bazel-skylib.git",
    tag = "0.3.1",
)

git_repository(
    name = "build_bazel_rules_apple",
    remote = "https://github.com/bazelbuild/rules_apple.git",
    tag = "0.4.0",
)