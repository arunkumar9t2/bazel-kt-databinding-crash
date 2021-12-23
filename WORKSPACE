load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_JVM_EXTERNAL_TAG = "4.2"

http_archive(
    name = "rules_jvm_external",
    sha256 = "cd1a77b7b02e8e008439ca76fd34f5b07aecb8c752961f9640dea15e9e5ba1ca",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")


bind(
    name = "databinding_annotation_processor",
    actual = "//tools:compiler_annotation_processor",
)

android_sdk_repository(
    name = "androidsdk",
    api_level = 30,
    build_tools_version = "30.0.3", # Build tools 31+ is not supported https://github.com/bazelbuild/bazel/issues/10240#issuecomment-884419566
)

http_archive(
    name = "io_bazel_rules_kotlin",
    sha256 = "6cbd4e5768bdfae1598662e40272729ec9ece8b7bded8f0d2c81c8ff96dc139d",
    urls = ["https://github.com/bazelbuild/rules_kotlin/releases/download/v1.5.0-beta-4/rules_kotlin_release.tgz"],
)

load("@io_bazel_rules_kotlin//kotlin:repositories.bzl", "kotlin_repositories")

kotlin_repositories()

load("@io_bazel_rules_kotlin//kotlin:core.bzl", "kt_register_toolchains")

kt_register_toolchains()


load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "grab_bazel_common",
    commit = "5f441bccbeca5d3e8530647035e5db2b1708897c",
    remote = "https://github.com/pswaminathan/grab-bazel-common.git",
)

# http_archive(
#     name = "grab_bazel_common",
#     sha256 = "9f53b1a95ac20dbef11ef2e9fa23aa9632209aa3fa7a0047d87696a61bb073a1",
#     urls = ["https://github.com/grab/grab-bazel-common/archive/240a1c393180c5121032e82e4603a124544c241b.zip"],
#     strip_prefix = "grab-bazel-common-240a1c393180c5121032e82e4603a124544c241b",
# )
# local_repository(
#     name = "grab_bazel_common",
#     path = "/Users/p/Code/grab-bazel-common",
# )

load("@grab_bazel_common//:workspace_defs.bzl", "GRAB_BAZEL_COMMON_ARTIFACTS")

DAGGER_TAG = "2.40.5"
http_archive(
    name = "dagger",
    sha256 = "5a6923e56edbc1e34c8089ecab5338a1b8ddb79a3a54b6c86cdcf31212680d32",
    strip_prefix = "dagger-dagger-%s" % DAGGER_TAG,
    urls = ["https://github.com/google/dagger/archive/dagger-%s.zip" % DAGGER_TAG],
)
load("@dagger//:workspace_defs.bzl", "DAGGER_ARTIFACTS", "DAGGER_REPOSITORIES")


maven_install(
    artifacts = GRAB_BAZEL_COMMON_ARTIFACTS + DAGGER_ARTIFACTS + [
        # "com.google.dagger:dagger:2.35.1",
        # "com.google.dagger:dagger-compiler:2.35.1",
        # "com.google.dagger:dagger-producers:2.35.1",
        # "com.squareup.moshi:moshi:1.9.2",
        'androidx.core:core-ktx:1.3.2',
        "com.google.android.material:material:1.3.0",
        "com.squareup.moshi:moshi-kotlin-codegen:1.12.0",
        "androidx.databinding:databinding-adapters:3.4.2",
        "androidx.databinding:databinding-common:3.4.2",
        "androidx.databinding:databinding-compiler:3.4.2",
        "androidx.databinding:databinding-runtime:3.4.2",
    ],
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)
