# Add Redis with Cloud Native Buildpacks

Add the `redis-cli` and `redis-server` CLIs to your application with Cloud Native Buildpacks.

Redis is built from source, but only once. Thanks to Cloud Native Buildpacks's rebaseable run layer, and caching support, each version of Redis will only ever be compiled once.

## Examples

Install Redis:

```plain
$ pack build redis-app --buildpack . --path . \
    --builder cloudfoundry/cnb:bionic
$ docker run -ti redis-app bash
cnb@1a08ed47cfbf:/workspace$ redis-cli -v
redis-cli 5.0.5
```

The first time the `redis-app` image is built, Redis will be built from source. On all subsequent builds it will be reused from the cache layer.

It will install the latest v5 Redis by default.

You can choose the latest v4 Redis with `$REDIS_MAJOR_VERSION=4`:

```plain
$ pack build redis-app --buildpack . --path . \
    --builder cloudfoundry/cnb:bionic \
    -e REDIS_MAJOR_VERSION=4

$ docker run -ti redis-app bash
cnb@1a08ed47cfbf:/workspace$ redis-cli -v
redis-cli 4.0.14
```

## Download dependencies

Whilst `bin/build` can download dependencies on demand, it is lovely for the dependencies to already be local when the buildpack is used (e.g. within a Builder).

Prior to using the buildpack, or including it in a Builder, download the `[[metadata.dependencies]]` into `vendor/` folder:

```plain
./bin/vendor-assets
```

It will verify their sha256 values.
