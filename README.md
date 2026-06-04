# Homebrew Tap for ridinCLIgun

Homebrew formula for ridinCLIgun [[GitHub](https://github.com/inference-garden/ridinCLIgun)] · [[Product Page](https://inference-garden.dev/en/products/ridincligun.html)] —
a terminal companion that advises but never acts (macOS).

## Install
Now finally easy to install :-)

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

- Project (GitHub): https://github.com/inference-garden/ridinCLIgun
- Product page: https://inference-garden.dev/en/products/ridincligun.html
- License: GPL-3.0-or-later
