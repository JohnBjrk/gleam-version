# Gleam Version Github Action

Parse `gleam.toml` and output the version set for key `gleam` (min version)

## Example

```yaml
jobs:
  get_version:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3.2.0
      - uses: johnbjrk/gleam_version@v1
        id: gleam-version
        with:
          fallback-version: 0.32.2
      - run: |
          echo $GLEAM_VERSION
        env:
          GLEAM_VERSION: ${{ steps.gleam-version.outputs.gleam-version }}
```

> NOTE: `fallback-version` is optional, but if it is not provided the step will fail if it cannot find `gleam.toml` with the key `gleam`
