# CoinRender Rust dependency fixes

This repository holds the separately versioned dependency sources used by the
experimental CoinRender bridge. Coin itself consumes these crates through Cargo
Git dependencies pinned to an immutable commit. It is not an upstream release.

The initial commit contains the published crate source subset previously used by
CoinRender, with unchanged normalized Cargo manifests. The following commit
applies the CoinRender corrections. Original upstream licenses remain inside each
crate directory. The crates keep their upstream package names and versions.

| Crate release | Original upstream Git commit | Upstream directory |
| --- | --- | --- |
| `glow-0.16.0` | `83c7b9b59ec4b26942801b3d0164db6d396a8c74` | `.` |
| `naga-24.0.0` | `dc1e50e08cd4a5c8d6c3e8a180e93535d40bec4a` | `naga` |
| `wgpu-core-24.0.5` | `99e6524b2b03cc35733f199bb5cb28787e8d42de` | `wgpu-core` |
| `wgpu-hal-24.0.4` | `993fc39b07e8a4418a15043265298d7bc016d059` | `wgpu-hal` |

Sources correspond to gfx-rs/wgpu for Naga, wgpu-core and wgpu-hal, and
grovesNL/glow for glow. The upstream commits above come from the published
crates' `.cargo_vcs_info.json`; the source layout uses their published normalized
Cargo manifests rather than the upstream workspace manifests.

Source and license files remain subject to each upstream crate's own licenses.
The dependency corrections and their reasons are documented in Coin's
`cmake/patches/rust-dependencies/` directory. They cover shader lowering,
GLES/Vulkan resource lifecycle and synchronization, and thread-local teardown.

Updating this repository does not update a Coin build: Coin's Cargo.toml and
Cargo.lock must explicitly select a new Git commit. Keep platform and GPU
qualification scoped to the tested Coin/dependency revisions.
