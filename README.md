# filen-cli-armv7

Unofficial CI that cross-compiles [`filen-cli`](https://github.com/FilenCloudDienste/filen-rs)
for 32-bit ARM Android (`armv7-linux-androideabi`), to run in Termux.

- Run: Actions tab -> `build-filen-cli-armv7` -> Run workflow (or `gh workflow run build.yml -R koedx/filen-cli-armv7`).
- Output: a GitHub Release holding `filen-cli-armv7-android` and `tls-patch.diff`.
- Patch: upstream's Android TLS check needs a JVM (JNI), which a Termux binary lacks;
  the workflow removes `"android"` from `PLATFORM_NET_TARGET_OSES` in `filen-sdk-rs/build.rs`
  so it uses bundled rustls roots instead.
- Status: UNVERIFIED until the first successful run is tested on the device.

Upstream is AGPL-3.0; this repo only contains the build workflow.
