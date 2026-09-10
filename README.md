# homebrew-loopsmith

Homebrew tap for [loopsmith](https://github.com/bitphill/loopsmith) — self-evolving
agent loops behind a deterministic verification gate.

```bash
brew tap bitphill/loopsmith
brew install loopsmith
```

Or in one line, without tapping:

```bash
brew install bitphill/loopsmith/loopsmith
```

Those are the only two forms Homebrew accepts. A two-component
`brew install bitphill/loopsmith` is not a formula reference — Homebrew reads it as
a core formula named `loopsmith` and answers `No available formula with the name
"loopsmith"`.

On Homebrew 6 and later both forms need `brew trust bitphill/loopsmith` once
first. Without it you get

```
Error: Refusing to load formula bitphill/loopsmith/loopsmith from untrusted tap bitphill/loopsmith.
```

It is a one-time acknowledgement per tap that you have decided to run someone
else's build instructions, and it is per tap rather than per formula. Older
Homebrew does not need it.

The formula builds from source and needs Rust only at build time
(`depends_on "rust" => :build`), so no Rust toolchain is left behind afterwards.

## Once it is installed

You do not have to learn the config format first. Two guided front ends build one
*for* you, asking one question at a time and explaining every field as they go:

```bash
loopsmith --web        # in your browser; offers a walk-through if you are new
loopsmith --guided     # the same questions in the terminal, no browser needed
```

`--web` opens on `127.0.0.1` only and asks whether you have done this before. Say
no and it explains what a loop is, offers a ready-made one to start from, and
walks you through the rest a card at a time. `--guided` asks the same questions in
a bare terminal, which is the one to reach for over SSH.

Neither runs anything or spends anything while you answer — you are writing a
description, and nothing happens until you press a button.

**Not a developer?** Start with the plain-English guide:
[README-FOR-DUMMIES.md](https://github.com/bitphill/loopsmith/blob/main/README-FOR-DUMMIES.md).

**Reading the code?** There is a generated code wiki, the same pages on two
surfaces: a [browsable viewer](https://bitphill.github.io/loopsmith/wiki/#overview)
and the [GitHub Wiki](https://github.com/bitphill/loopsmith/wiki).

## Why a tap rather than homebrew-core

A formula in `homebrew-core` would make the tap step unnecessary. That route needs
a review PR against a repository with more history behind it than loopsmith has
yet — Homebrew asks that upstream be maintained, notable, and shipping immutable
tagged releases before it takes on the maintenance burden. `Formula/loopsmith.rb`
is written to core's conventions (`std_cargo_args`, a real `test do` block, no
`head`-only tricks) so the same file can be submitted when that day comes.

## Updating the formula

`url` points at the GitHub source tarball for a tag, and `sha256` is that
tarball's digest:

```bash
curl -sL https://github.com/bitphill/loopsmith/archive/refs/tags/v0.1.0.tar.gz | shasum -a 256
```

The canonical copy of the formula lives in the main repository at
`Formula/loopsmith.rb`; this tap mirrors it.

MIT licensed, as loopsmith is.
