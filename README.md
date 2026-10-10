# hachi

`hachi` is the command line for [hachiflow](https://hachiflow.com): hire agents, send them work and approve what they do, from a terminal or from another agent. This repository holds release binaries only. There is no source here.

## Install

```sh
brew install hachiflow/tap/hachi
hachi version
```

Or download an archive for macOS, Linux or Windows (amd64 and arm64) from the [releases](https://github.com/hachiflow/hachi/releases) page. Each release carries `checksums.txt`, an SBOM per archive and a keyless cosign signature of the checksums (`checksums.txt.sig`).

## The contract

`hachi` is built to be driven by a model.

- stdout is always JSON: one document, an NDJSON stream, or a typed error. Never prose.
- Errors are `{"error":{"kind","code","reason","message","hint"}}` on stdout plus one `error[kind]: message` line on stderr.
- One stable exit code per error kind. Nothing prompts when stdin is not a terminal.
- Secrets arrive on stdin (`--token-stdin`), never as arguments.
- `hachi version` prints `{"tool","version","commit","date","go","os","arch"}`.
- `hachi schema` prints every command, flag, input and output as JSON Schema. `hachi llms` prints a short guide for a model.

## Docs

Start with `hachi llms` and `hachi schema`, which ship inside the binary and always match it. More at [hachiflow.com](https://hachiflow.com).
