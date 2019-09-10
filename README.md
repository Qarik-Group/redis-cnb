# Add Redis with Cloud Native Buildpacks

Add the `redis-cli` and `redis-server` CLIs to your application with Cloud Native Buildpacks.

## Examples

Install Redis:

```plain
$ pack build redis-app --buildpack . --path . \
    --builder cloudfoundry/cnb:bionic
$ docker run -ti redis-app bash
cnb@1a08ed47cfbf:/workspace$ redis-cli -v
redis-cli 5.0.5

```

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
