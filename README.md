# GitHub Action to setup gRPC C++ environment

![CI](https://github.com/eWaterCycle/setup-grpc/workflows/build-test/badge.svg)
![Validate versions](https://github.com/eWaterCycle/setup-grpc/workflows/Validate%20'setup-grpc'/badge.svg)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3964180.svg)](https://doi.org/10.5281/zenodo.3964180)

To compile C++ code against gRPC in a GitHub action workflow you need to install it first. This GitHub action compiles or downloads it for you.

Installation follows [gRPC build instructions](https://github.com/grpc/grpc/blob/master/BUILDING.md).

* The bin directory is added to the `PATH` env var
* The lib directory is added to `LD_LIBRARY_PATH` env
* `GRPC_ROOT` env var is set to install directory.
* The install directory is added to the `CMAKE_PREFIX_PATH` env var
* Installation includes protobuf installation
* Besides C++ gRPC plugin, plugins for Node, PHP, Python, Ruby are also made

## Inputs

### `grpc-version`

Version of gRPC. See [releases page](https://github.com/hpcng/grpc/releases) for available versions. If a binary build of a version is available on [https://github.com/eWaterCycle/grpc-versions/releases](https://github.com/eWaterCycle/grpc-versions/releases) it is used otherwise the version is build during the action, which takes significantly longer. Versions lower then 3.6 need additional OS packages installed like `uuid-dev`.

## Example usage

```yaml
steps:
- uses: actions/checkout@v2
- uses: eWaterCycle/setup-grpc@v2
  with:
    grpc-version: 1.30.2
```

## Build

For developers of setup-grpc action.

Install deps with

```bash
npm install
```

Build dist with

```bash
npm run build
```
