# check_kubelet_version.sh

## Description

This bash script will retieve the Kubernetes upstream release for the desired RHOCP releases

The script has the following dependencies:

- `oc`
  - Please download from:  <https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/>
- `jq`
  - To download on Linux: `yum install jq`
  - To download on MacOS: `brew install jq`

## Usage

### Basic Usage

Simply run the script with the desired option(s)

```bash
usage: check_kubelet_version.sh -r <release> | -m <minor_version> [-a <Arch>] [-k] [-h]
```

### Script Options

```text
usage: check_kubelet_version.sh -r <release> | -m <minor_version> [-a <Arch>] [-k] [-h]
|------------------------------------------------------------------------------------------------------------|
| Options | Description                                                     | [Defaults]                     |
|---------|-----------------------------------------------------------------|--------------------------------|
|      -r | List of release version(s) to check                             |                                |
|      -m | List of minor version(s) to check                               |                                |
|      -a | Architecture used to check the image                            | x86_64                         |
|      -k | Display the output as KCS format                                | false                          |
|---------|-----------------------------------------------------------------|--------------------------------|
|         | Additional Options:                                             |                                |
|---------|-----------------------------------------------------------------|--------------------------------|
|      -h | display this help and check for updated version                 |                                |
|------------------------------------------------------------------------------------------------------------|

Current Version: X.Y.Z
```

### Examples

- Check multiple releases _(default archictecture)_.

  ```bash
  check_kubelet_version.sh -r 4.14.0,4.15.0,4.16.0 -r 4.17.0
  ```

- Check the RHOCP minor versions _(default archictecture)_, formatting the output in KCS table.

  ```bash
  check_kubelet_version.sh -p ./<pull_secret_file> -m 4.16,4.17 -m 4.15 -k
  ```

- Mixing Release and Minor versions.

  ```bash
  check_kubelet_version.sh -p ./<pull_secret_file> -a x86_64 -r 4.14.0,4.15.0 -m 4.16
  ```
