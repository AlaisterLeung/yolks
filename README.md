# Yolks for Alaister.net

A curated collection of core images that can be used with Pterodactyl's Egg system. Each image includes Alaister.net
custom startup script and is rebuilt periodically to ensure dependencies are always up-to-date.

Images are hosted on `ghcr.io` and exist under the `yolks` space.

All of these images are available for `linux/amd64` version, unless otherwise specified.

### Contributing

When adding a new version to an existing image, such as `java v69`, you'd add it within a child folder of `java`, so
`java/69/Dockerfile` for example. Please also update the correct `.github/workflows` file to ensure that this new version
is tagged correctly.

## Available Images
See https://github.com/orgs/alaister-net/packages/container/package/yolks
