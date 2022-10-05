# Read node version from engines field in package.json

Read your node version from `package.json`

## Example workflow

`package.json`
```json

{
  "name": "your-package",
  "engines": {
    "node": "12.13.x"
  }
}
```

`.github/workflow/test.yml`
```yml
name: Get node version from package.json

on: push

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: Read node from package.json
        uses: culshaw/read-package-node-version-actions@v1
        id: package-node-version

      - name: Show node version number
        run: echo "Version is ${{ steps.package-node-version.outputs.version }}"
        # Version is 12.13.x
```

## Inputs

### path

Path of `package.json`, `./` by default.

`path/to/package.json`
```json

{
  "name": "your-package",
  "engines": {
    "node": "12.13.x"
  }
}
```

```yml
name: Get version from package.json

on: push

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: Read node from package.json
        uses: culshaw/read-package-node-version-actions@v1
        with: 
          path: "./path/to/package.json"
        id: package-node-version

      - name: Show version number
        run: echo "Version is ${{ steps.package-node-version.outputs.version }}"
        # Version is 12.13.x
```

# License

MIT