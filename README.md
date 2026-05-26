# inifix-pre-commit

This repository provides two `pre-commit` hooks on top of `inifix` (and its companion
command line interface, `inifix-cli`):
- `inifix-validate`
- `inifix-format`

Both these hooks can be configured by adding the following snippets to
`.pre-commit-config.yaml`

```yaml
  - repo: https://github.com/la-niche/inifix-pre-commit.git
    rev: v1.0.1
    hooks:
      - id: inifix-validate
```
or
```yaml
  - repo: https://github.com/la-niche/inifix-pre-commit.git
    rev: v1.0.1
    hooks:
      - id: inifix-format
```

Note that `inifix-format` also validates data by default, so it is redundant to
enable both hooks with no further configuration. Validation and formatting may
nonetheless be decoupled as
```patch
  - repo: https://github.com/la-niche/inifix-pre-commit.git
    rev: v1.0.1
    hooks:
    - id: inifix-validate
    - id: inifix-format
+     args: [--skip-validation]
```

## Selecting files

By default, both hooks target files matching the regular expression `(\.ini)$`.
It is possible to override this expression as, e.g.,
```patch
   hooks:
   - id: inifix-format
+    files: (\.ini|\.par)$
```

For convenience, in cases where the appropriate regular expression is hard to write,
for instance if your project contains some files with a `.ini` extension that are not
intended to be used with idefix, you may refine the selection via exclude patterns,
using `--exclude` and/or `--extend-exclude`. By default, files named `pytest.ini` or
`tox.ini` are excluded.

## Dependencies

This repository serves a minimal Python metapackage, which pins *all* dependencies
exactly (including the build backend), with the goal of making it as resilient as
possible to supply chain attacks.

As of version 1.0.1, the entire dependency tree is as follow
- `inifix-cli==1.1.0`
  - `inifix==7.0.0`
  - `click==8.3.3`
    - `colorama==0.4.6` (Windows only)
- `flit-core==3.12.0` (build time)

