# homebrew-loopsmith

Homebrew tap for [loopsmith](https://github.com/bitphill/loopsmith) — self-evolving
agent loops behind a deterministic verification gate.

```bash
brew tap bitphill/loopsmith
brew install loopsmith
```

Once tapped, the bare name resolves, so `brew install loopsmith` is all that is
needed on subsequent machines that already have the tap. Without the tap, use the
fully qualified name:

```bash
brew install bitphill/loopsmith/loopsmith
```

The formula builds from source and needs Rust only at build time
(`depends_on "rust" => :build`), so no Rust toolchain is left behind afterwards.

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
