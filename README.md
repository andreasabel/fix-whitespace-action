# fix-whitespace-action

Run [`fix-whitespace`](https://github.com/agda/fix-whitespace) on your repository.
The `fix-whitespace` tool checks for absense of _whitespace violations_, which are tabs, trailing whitespace, and lack of newline character at the end of the file.
Files which should be checked are specified in the configuration file, typically `fix-whitespace.yaml` in the repository root.


Standard use:
```
steps:
  - uses: actions/checkout@v3
  - uses: andreasabel/fix-whitespace-action@v1
```
This downloads the `fix-whitespace` binary, installs it into `~/.local/bin` and runs it with standard parameters on the repository root.

Example using all parameters:
```
steps:
  - uses: actions/checkout@v3
  - uses: andreasabel/fix-whitespace-action@v1
    with:
      version:    0.0.10
      configfile: fix-whitespace.yaml
      fix:        true

```
Setting `fix: true` fixes whitespace violations in place.
Of course, these are fixed only in the checked-out version on the runner.
You may be able to push these fixes pack to your repository, e.g., by opening a PR on your repository.

Input `version` refers to the [version of the `fix-whitespace` program](https://github.com/agda/fix-whitespace/releases).

With input `configfile` one can specify the configuration file (defaults to `fix-whitespace.yaml`).
