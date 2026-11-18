# Helium Client

Helium Client is a Minecraft client project built around **Helium Render Engine**, with a focus on smoother play on low-end PCs.

Repository: [GxpixamoDev/HeliumClient](https://github.com/GxpixamoDev/HeliumClient)

## Development status

This workspace contains an existing Rust client and launcher derived from Horizon. Helium is in development. Features inherited from Horizon, experimental Helium changes, and measured results must be distinguished before release. No universal FPS improvement or Java mod compatibility is promised.

## Helium Render Engine

The engine's performance priorities are:

- **Lighting:** reduce redundant light updates and chunk rebuilds while preserving correct block light, sky light, and chunk boundaries.
- **Render scale:** reduce GPU load with configurable internal resolution and measured scaling behavior.
- **Frame generation:** investigate optional intermediate frames with correct history handling, HUD presentation, and HDR preservation. Generated frames must be reported separately from rendered frames; they do not increase simulation speed.
- **Low-end smoothness:** control background work, mesh uploads, and allocations to reduce frame-time spikes during movement and chunk loading.

These are development objectives, not verified performance claims. Validation should report hardware, resolution, render distance, settings, average FPS, 1% lows, and frame-time percentiles using identical scenes before and after changes.

## Mods and compatibility

Java performance mods serve as references for behavior and architecture. Their JAR files cannot be assumed to run inside a Rust client. Each feature requires an explicit native implementation or a verified compatibility layer.

Horizon content mods, native code mods, shader packs, and resource packs use different interfaces. Compatibility depends on the pinned engine version and must be tested per package. See [Horizon documentation](https://playhorizon.dev/docs/) and [mod documentation](https://github.com/horizon-rust/horizon/blob/main/docs/mods.md).

## Local workspace

- `horizon-main/`: current Helium source, launcher, and build instructions in `helium/README.md`.
- `horizon-work/`: older reference snapshot; not the active implementation.
- `releases/`: local release artifacts; validation applies to each individual build.

Minecraft assets, game JARs, prepared resources, account credentials, and personal saves must not be committed. Use a legally obtained Minecraft installation and isolated test worlds.

## Source and distribution policy

Helium-owned original code is intended to be proprietary and is not offered under an open-source license unless explicitly stated. No permission to redistribute or reuse that original code is granted by this README.

Third-party code retains its own licenses and copyright notices. This policy does not replace or restrict rights granted by those licenses. The local Horizon snapshots include an MIT license; newer upstream revisions may carry different terms. Review the exact source revision and dependency notices before importing or distributing changes. Preserve `LICENSE` and `THIRD_PARTY_NOTICES.md` with the relevant source and distributions.

A README does not make a GitHub repository private. Keep proprietary source in a private repository; use a separate public repository for product information and approved releases if desired.

## Credits

Helium Client is maintained by GxpixamoDev. Horizon and its contributors provide the existing Rust foundation; see the preserved upstream notices. Helium Render Engine is the name of Helium's rendering work and does not imply ownership of third-party code.

Not an official Minecraft product. Not approved by or associated with Mojang or Microsoft.
