# homebrew-anime-sh

Homebrew tap for **[anime-sh](https://github.com/Anime123450/anime-sh)** — watch anime from your terminal.

```bash
brew tap Anime123450/anime-sh
brew install anime-sh
anime
```

> **This takes a while — about 25 minutes on macOS.** A tap has no prebuilt
> bottles, so Homebrew compiles every dependency from source, and two of them
> are slow: `pydantic-core` is Rust and `Pillow` is C against the image
> libraries. It is a one-off; upgrades reuse what is already built.
>
> If you would rather not wait, and you do not mind Python being involved:
>
> ```bash
> uv tool install "anime-sh[tui]"   # seconds, from wheels
> brew install mpv                  # still needed to play anything
> ```


mpv is installed with it. Downloads (`anime download`, `anime prefetch`) also
need ffmpeg:

```bash
brew install ffmpeg
```

Run `anime doctor` to check everything at once, or `anime doctor --streams` to
see which sources actually work from your connection.

## macOS and Linux

The formula builds anime-sh into its own virtualenv from PyPI sdists, so it
works on both Apple silicon and Intel macOS, and on Linuxbrew.

## Updating the formula

The formula is generated, not hand-edited — it pins a sha256 for every
transitive dependency, which is not something to maintain by hand. After a
release, from the anime-sh repo:

```bash
uv run python scripts/brew_formula.py --version <new-version> > Formula/anime-sh.rb
```
