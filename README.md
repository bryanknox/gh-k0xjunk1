# A simple C# sample GitHub CLI Extension

A sample GitHub CLI Extension implemented in C# .NET.

The code includes a GitHub Actions workflow that:
- Builds and packages the sample extension for multiple platforms.
- Publishes releases of the sample extension.

# Technologies
- C#
- .NET 8.0
- [GitHub CLI](https://cli.github.com/)
- GitHub Actions
  - [softprops/action-gh-release](https://github.com/softprops/action-gh-release/tree/v1/)
- [Dev Containers](https://containers.dev/)

## Installation of the sample GitHub CLI Extension

Install the [GitHub CLI](https://cli.github.com/).

Install:

```shell
gh extension install bryanknox/gh-k0xjunk1
```

Upgrade:

```shell
gh extension upgrade k0xjunk1
```

Uninstall:

```shell
gh extension remove k0xjunk1
```

## Usage of the sample GitHub CLI Extension
The extension adds a `k0xjunk1` command to the GitHub CLI.

```bash
gh k0xjunk1
```
It simply outputs a short greeting message.

## Developer Notes

### Dev Container
This repo includes a [Dev Container](https://containers.dev/)
that eleminates the need to install the [GitHub CLI](https://cli.github.com/), .NET 8.0 SDK, and other tools on your local machine.

If you're using VS Code see [Developing inside a Container](https://code.visualstudio.com/docs/devcontainers/containers).

## Building and Packaging the sample GitHub CLI Extension

A build of the sample extension is triggered on push to `main` or by pull request.

The `build` job defined in the `.github\workflows\ci.yml` file shows how the extension is built and then packaged for multiple target platforms.

## Creating Releases the sample GitHub CLI Extension

### Create a Draft Release of the Extension
A draft release is created in the repo when a tag with a 'v' prefix is pushed to 'main'. For example:
```shell
git tag v1.2.3
git push origin v1.2.3
```
A new build of the extension will be triggered, and a draft release with the given tag will be created.

The `publish` job defined in the `.github\workflows\ci.yml` file shows how the draft release is created for the built and packaged extension.

The [softprops/action-gh-release](https://github.com/softprops/action-gh-release/tree/v1/) GitHub Action is used to create the draft release.


### Publishing a Release of the Extension
A draft release can be published by simply editing the release and switching it from draft to published.

That can be done using the GitHub CLI. For example:

```shell
gh release edit v1.2.3 --draft=false
```

Once the release is published the extension can be installed as described above.
