# Homebrew Tap for ridinCLIgun

Homebrew formula for [ridinCLIgun](https://github.com/inference-garden/ridinCLIgun) —
a terminal companion that advises but never acts (macOS).

## Install

```bash
brew tap inference-garden/ridincligun
brew install ridincligun
```

Then run `ridincligun`. The local advisory features work with no API key; add an
`ANTHROPIC_API_KEY`, `OPENAI_API_KEY`, or `MISTRAL_API_KEY` to enable AI review.
All three provider SDKs are bundled.

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

- Project: https://github.com/inference-garden/ridinCLIgun
- License: GPL-3.0-or-later
