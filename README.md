# Homebrew Tap for ridinCLIgun

Homebrew formula for ridinCLIgun [[GitHub](https://github.com/inference-garden/ridinCLIgun)] · [[Product Page](https://inference-garden.dev/en/products/ridincligun.html)] —
a terminal companion that advises but never acts (macOS).

## Install
Now finally easy to install :-)

```bash
brew tap inference-garden/ridincligun
brew install ridincligun
```

When a prebuilt bottle is available for your macOS version and architecture
(Apple Silicon and Intel are both covered), the install pours it in seconds —
no compiler toolchain is downloaded. On combinations without a bottle,
Homebrew transparently builds from source instead (this pulls the Rust
toolchain and takes a few minutes, but works the same).

Then run `ridincligun`. The local advisory features work with no API key; add an
`ANTHROPIC_API_KEY`, `OPENAI_API_KEY`, or `MISTRAL_API_KEY` to enable AI review.
All three provider SDKs are bundled.

### Tap trust

Newer Homebrew versions can require third-party taps to be explicitly trusted
(`HOMEBREW_REQUIRE_TAP_TRUST`, default in Homebrew 6). If your install is
refused with a trust error, run:

```bash
brew trust inference-garden/ridincligun
```

and retry. `brew untrust inference-garden/ridincligun` reverses it.

### Installed earlier from source?

If you installed before bottles existed, your machine downloaded the `rust`
and `llvm` build toolchain (~2 GB) — it is no longer needed and can be
reclaimed:

```bash
brew autoremove
```

### Build from source on purpose

```bash
brew install --build-from-source ridincligun
```

## Upgrade

```bash
brew upgrade ridincligun
```

## Uninstall

```bash
brew uninstall ridincligun
brew untap inference-garden/ridincligun
```

## Links

- Project (GitHub): https://github.com/inference-garden/ridinCLIgun
- Product page: https://inference-garden.dev/en/products/ridincligun.html
- License: GPL-3.0-or-later
