# Add Redis with Cloud Native Buildpacks

Add the `redis-cli` and `redis-server` CLIs to your application with Cloud Native Buildpacks.

## Examples

Install Redis:

```plain
pack build redis-app --no-pull --buildpack . --path .
```

Install a specific version of Redis that is supported within `buildpack.toml`:

```plain
pack build redis-app --no-pull --buildpack . --path . -e REDIS_VERSION=4.0.14
```

Install a specific version of Redis that can be downloaded from Internet:

```plain
pack build redis-app --no-pull --buildpack . --path . \
    -e REDIS_VERSION=4.0.14 \
    -e ACCEPT_REDIS_DOWNLOAD=1
```
