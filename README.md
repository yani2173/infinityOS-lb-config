# ester platforms-lb-config
Live-build configuration for the ester project.

## Build sequence

```sh
docker build -t infinityos-build .
docker run --privileged -v "$(pwd):/build/config" infinityos-build
```

- `docker build` creates the Debian 13 (trixie) image with `live-build` and the tools it needs.
- `docker run --privileged` bind-mounts this repo as `/build/config` and runs `build.sh`, which calls `lb config` (sets distro, arch, bootloaders, mirrors) and `lb build` (assembles the ISO).
- Output is the resulting `.iso` file in the working directory after the run finishes.
