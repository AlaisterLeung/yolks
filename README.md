# Yolks for Alaister.net

A curated collection of core images that can be used with Pterodactyl's Egg system. Each image is rebuilt
periodically to ensure dependencies are always up-to-date.

Images are hosted on `ghcr.io` and exist under the `yolks` space. The following logic
is used when determining which space an image will live under:

* `yolks` — these are more generic images that allow different types of games or scripts to run. They're generally just
a specific version of software and allow different Eggs within Pterodactyl to switch out the underlying implementation. An
example of this would be something like Java or Python which are used for running bots, Minecraft servers, etc.

All of these images are available for `linux/amd64` version, unless otherwise specified.

### Contributing

When adding a new version to an existing image, such as `java v69`, you'd add it within a child folder of `java`, so
`java/69/Dockerfile` for example. Please also update the correct `.github/workflows` file to ensure that this new version
is tagged correctly.

## Available Images
See https://github.com/users/AlaisterLeung/packages/container/package/yolks
