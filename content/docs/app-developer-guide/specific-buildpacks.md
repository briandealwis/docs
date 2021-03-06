+++
title="Specify buildpacks"
weight=4
summary="Learn how to specify exactly what buildpacks are used during the build process."
+++

{{< param "summary" >}}

### `--buildpacks`

The `--buildpack` parameter can be one of the following:

- path to a directory<sup><small>†</small></sup>, `tar` file, or `tgz` file
- URL to a `tar` or `tgz` file
- buildpack located in a builder, in the form of `<id>[@<version>]`<sup><small>‡</small></sup>
- image name

<small><sup>†</sup> Directory buildpacks are not currently supported on Windows.</small><br />
<small><sup>‡</sup> Version may be omited if there is only one buildpack in the builder matching the `id`.</small>

##### Example:

For this example we will use a few buildpacks from our [samples][samples] repo.

```bash
# clone the repo
git clone https://github.com/buildpacks/samples

# build the app
pack build sample-java-maven-app \
    --builder cnbs/sample-builder:alpine \
    --buildpack samples/java-maven \
    --buildpack samples/buildpacks/hello-processes/ \
    --buildpack cnbs/sample-package:hello-universe \
    --path samples/apps/java-maven/
```

> Multiple buildpacks can be specified, in order, by supplying:
>
> - `--buildpack` multiple times, or
> - a comma-separated list to `--buildpack` (without spaces)

[samples]: https://github.com/buildpacks/samples