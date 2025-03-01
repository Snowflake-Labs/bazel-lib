<!-- Generated with Stardoc: http://skydoc.bazel.build -->

Public API for expand template

<a id="expand_template"></a>

## expand_template

<pre>
expand_template(<a href="#expand_template-name">name</a>, <a href="#expand_template-data">data</a>, <a href="#expand_template-is_executable">is_executable</a>, <a href="#expand_template-out">out</a>, <a href="#expand_template-stamp">stamp</a>, <a href="#expand_template-stamp_substitutions">stamp_substitutions</a>, <a href="#expand_template-substitutions">substitutions</a>, <a href="#expand_template-template">template</a>)
</pre>

Template expansion

This performs a simple search over the template file for the keys in substitutions,
and replaces them with the corresponding values.

Values may also use location templates as documented in
[expand_locations](https://github.com/aspect-build/bazel-lib/blob/main/docs/expand_make_vars.md#expand_locations)
as well as [configuration variables](https://docs.bazel.build/versions/main/skylark/lib/ctx.html#var)
such as `$(BINDIR)`, `$(TARGET_CPU)`, and `$(COMPILATION_MODE)` as documented in
[expand_variables](https://github.com/aspect-build/bazel-lib/blob/main/docs/expand_make_vars.md#expand_variables).


**ATTRIBUTES**


| Name  | Description | Type | Mandatory | Default |
| :------------- | :------------- | :------------- | :------------- | :------------- |
| <a id="expand_template-name"></a>name |  A unique name for this target.   | <a href="https://bazel.build/docs/build-ref.html#name">Name</a> | required |  |
| <a id="expand_template-data"></a>data |  List of targets for additional lookup information.   | <a href="https://bazel.build/docs/build-ref.html#labels">List of labels</a> | optional | [] |
| <a id="expand_template-is_executable"></a>is_executable |  Whether to mark the output file as executable.   | Boolean | optional | False |
| <a id="expand_template-out"></a>out |  Where to write the expanded file.   | <a href="https://bazel.build/docs/build-ref.html#labels">Label</a> | required |  |
| <a id="expand_template-stamp"></a>stamp |  Whether to encode build information into the output. Possible values:<br><br>    - <code>stamp = 1</code>: Always stamp the build information into the output, even in         [--nostamp](https://docs.bazel.build/versions/main/user-manual.html#flag--stamp) builds.         This setting should be avoided, since it is non-deterministic.         It potentially causes remote cache misses for the target and         any downstream actions that depend on the result.     - <code>stamp = 0</code>: Never stamp, instead replace build information by constant values.         This gives good build result caching.     - <code>stamp = -1</code>: Embedding of build information is controlled by the         [--[no]stamp](https://docs.bazel.build/versions/main/user-manual.html#flag--stamp) flag.         Stamped targets are not rebuilt unless their dependencies change.   | Integer | optional | -1 |
| <a id="expand_template-stamp_substitutions"></a>stamp_substitutions |  Mapping of strings to substitutions.<br><br>            There are overlayed on top of substitutions when stamping is enabled             for the target.<br><br>            Substitutions can contain $(execpath :target) and $(rootpath :target)             expansions, $(MAKEVAR) expansions and {{STAMP_VAR}} expansions when             stamping is enabled for the target.   | <a href="https://bazel.build/docs/skylark/lib/dict.html">Dictionary: String -> String</a> | optional | {} |
| <a id="expand_template-substitutions"></a>substitutions |  Mapping of strings to substitutions.<br><br>            Substitutions can contain $(execpath :target) and $(rootpath :target)             expansions, $(MAKEVAR) expansions and {{STAMP_VAR}} expansions when             stamping is enabled for the target.   | <a href="https://bazel.build/docs/skylark/lib/dict.html">Dictionary: String -> String</a> | optional | {} |
| <a id="expand_template-template"></a>template |  The template file to expand.   | <a href="https://bazel.build/docs/build-ref.html#labels">Label</a> | required |  |


