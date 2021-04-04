load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")

release = "1.10.0"
http_archive(
  name = "googletest",
  urls = ["https://github.com/google/googletest/archive/release-" + release + ".tar.gz"],
  strip_prefix = "googletest-release-" + release,
)

http_file(
  name = "cpplint_build",
  urls = ["https://raw.githubusercontent.com/nicmcd/pkgbuild/master/cpplint.BUILD"],
)

release = "1.5.4"
http_archive(
  name = "cpplint",
  urls = ["https://github.com/cpplint/cpplint/archive/" + release + ".tar.gz"],
  strip_prefix = "cpplint-" + release,
  build_file = "@cpplint_build//file:downloaded",
)

http_file(
  name = "clang_format",
  urls = ["https://raw.githubusercontent.com/nicmcd/pkgbuild/master/clang-format"],
)

http_file(
    name = "numa_build",
    urls = ["https://raw.githubusercontent.com/nicmcd/pkgbuild/master/numa.BUILD"],
)

http_file(
    name = "numa_patch",
    urls = ["https://raw.githubusercontent.com/nicmcd/pkgbuild/master/numactl_v2.0.14.patch"],
)

release = "2.0.14"
http_archive(
    name = "numactl",
    urls = ["https://github.com/numactl/numactl/archive/refs/tags/v" + release + ".tar.gz"],
    strip_prefix = "numactl-" + release,
    build_file = "@numa_build//file:downloaded",
    patches = ["@numa_patch//file:downloaded"],
    patch_args = ["-p1"],
    patch_cmds = ["./autogen.sh", "./configure"],
)
