load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library", "swift_test")

swift_library(
    name = "SwiftLintFrameworkTests.library",
    testonly = True,
    srcs = glob(
        ["SwiftLintFrameworkTests/**/*.swift"],
        exclude = [
            "SwiftLintFrameworkTests/Resources/**",
            # Bazel doesn't support paths with spaces in them
            "SwiftLintFrameworkTests/FileNameNoSpaceRuleTests.swift",
            # FIXME: Get these tests passing with Bazel
            "SwiftLintFrameworkTests/ConfigurationTests+Mock.swift",
            "SwiftLintFrameworkTests/ConfigurationTests+MultipleConfigs.swift",
            "SwiftLintFrameworkTests/ConfigurationTests.swift",
            "SwiftLintFrameworkTests/IntegrationTests.swift",
            "SwiftLintFrameworkTests/SourceKitCrashTests.swift",
        ],
    ),
    module_name = "SwiftLintFrameworkTests",
    deps = [
        "//:SwiftLintFramework",
    ],
)

swift_test(
    name = "SwiftLintFrameworkTests",
    data = glob(
        ["SwiftLintFrameworkTests/Resources/**"],
        # Bazel doesn't support paths with spaces in them
        exclude = ["SwiftLintFrameworkTests/Resources/FileNameNoSpaceRuleFixtures/**"],
    ),
    visibility = [
        "//Tests:__subpackages__",
    ],
    deps = [
        ":SwiftLintFrameworkTests.library",
    ],
)

swift_library(
    name = "ExtraRulesTests.library",
    testonly = True,
    srcs = [
        "SwiftLintFrameworkTests/ExtraRulesTests.swift",
        "SwiftLintFrameworkTests/TestHelpers.swift",
    ],
    module_name = "ExtraRulesTests",
    deps = [
        "//:SwiftLintFramework",
    ],
)

swift_test(
    name = "ExtraRulesTests",
    visibility = ["//visibility:public"],
    deps = [
        ":ExtraRulesTests.library",
    ],
)
