go_library(
    name = 'utils',
    srcs = glob(['*.go'], exclude = [
        'wrapper_script.go',
        'stub.go',
        '*_test.go',
    ]) + [':bindata'],
    deps = [
        '//src/core',
        '//third_party/go:levenshtein',
        '//third_party/go:logging',
        '//third_party/go:prompter',
    ],
    visibility = ['PUBLIC'],
)

go_bindata(
    name = 'bindata',
    srcs = [
        '//tools/misc:completion_script',
        '//tools/misc:wrapper_script',
    ],
    prefix = 'tools/misc',
)

go_test(
    name = 'utils_test',
    srcs = ['utils_test.go'],
    data = ['test_data/stdin.txt'],
    deps = [
        ':utils',
        '//third_party/go:testify',
    ],
)
