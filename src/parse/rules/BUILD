build_defs = glob(['*.build_defs'])

genrule(
    name = 'builtin_rules',
    srcs = build_defs,
    outs = [build_def + '.gob' for build_def in build_defs],
    cmd = '$TOOL -o $TMP_DIR $SRCS',
    tools = ['//src/parse/asp/main:compiler'],
)

go_bindata(
    name = 'builtin_data',
    srcs = build_defs + [':builtin_rules'],
)

go_library(
    name = 'rules',
    srcs = [':builtin_data'],
    visibility = ['//src/parse/...'],
)

gentest(
    name = 'lint_builtin_rules_test',
    data = build_defs + ['//tools/linter'],
    no_test_output = True,
    test_cmd = '$(location //tools/linter) $PKG/*.build_defs',
)
