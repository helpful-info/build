# Helpful Info - GitHub Action: `build`

> A GitHub Action for building instances of the [Helpful-Information App](https://github.com/rodekruis/helpful-information).

This GitHub Action should make it easier to build and prepare your instance before deploying it.
It tries to handle common build tasks and configurations automatically, reducing the need for manual setup.

## Supported version(s)

This action supports the following versions of the [Helpful-Information App](https://github.com/rodekruis/helpful-information/releases):

| `helpful-information` | Node.js | GitHub Action: `build` |
| --------------------- | ------- | ---------------------- |
| `v26.11.0`            | `v24`   | `v1`                   |

## Usage

To use this GitHub Action, include it in your workflow YAML file as follows:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v7

      - name: 'Build HIA-instance'
        uses: helpful-info/build@v1
        with: 
          includePublicFiles: true
          # ... And/or specify other options; See below.
```

### Automatic version-upgrades

When you specify the action version using `helpful-info/build@v1`, GitHub will automatically use the latest compatible release of the action (within the `v1` major version).  
This allows you to benefit from automatic updates and improvements without manually changing the version in your workflow.

Whenever there are changes to this action that will change the output significantly, or require changes to the supplied configuration/inputs, the major version will be incremented (i.e., from `v1` to `v2`) to signal potential breaking changes.

### Options

#### `publicUrl` (optional)

Specifies the public URL where your instance will be deployed.  
If not provided, the action will attempt to infer it from the repository name and workflow context.

#### `includePublicFiles` (optional)

Specifies whether to include public files in the build output.  
Defaults to `true` if not provided; To disable, use:

```yaml
- name: 'Build HIA-instance (without public-folder)'
  uses: helpful-info/build@v1
  with: 
    includePublicFiles: false
```

---

## Contribute

See: <https://github.com/rodekruis/helpful-information>

---

## License

Released under the Apache 2.0 License. See [LICENSE](./LICENSE).
