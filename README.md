# BlankOBF — archived research copy (neutered)

> [!WARNING]
> The script in this repository is a preserved copy of **BlankOBF** that has been **intentionally modified so that it no longer functions**. It cannot obfuscate anything, and every file it emits is inert. This is by design. It is published for research and documentation purposes only.

## What was BlankOBF?

BlankOBF was a free Python obfuscator written by **Blank-c**. It wraps a Python script in a stack of transformations:

1. `marshal`-compiled code object
2. base64, split into four parts — one rot13-encoded, one reversed — and reassembled at runtime
3. LZMA compression
4. a bootstrapped `eval` / `getattr` / `__import__` chain with machine-generated variable names, with all import references hidden behind base64

It shipped as the obfuscation component of **Blank Grabber**, an open-source Windows infostealer builder, where it was applied to the generated payload stub before PyInstaller packing (followed by postprocess string-patching and Authenticode signature grafting via SigThief).

## Why this repo exists

As of October 2026, all upstream repositories are gone (status verified 2026-10-14):

- `github.com/Blank-c/BlankOBF` — **404**
- `github.com/Blank-c/Blank-Grabber` — **404**
- `github.com/Blank-c` (account) — **404**

The upstream repositories appear to have been removed — either deleted by the author or taken down by GitHub. Copies of Blank Grabber nonetheless continue to circulate in malware build kits and stray mirrors. This repository preserves a copy of the obfuscator for researchers studying the Blank Grabber build pipeline, with the working logic disabled so that the archive itself is not usable as a tool.

## Provenance

Recovered from the **Blank Grabber v2.03** source distribution (`blankgrabberV2.03-main.zip`), path `Blank-Grabber-main/Blank Grabber/Components/BlankOBF.py`, during static analysis of a Blank Grabber payload sample.

| File | SHA-256 |
|---|---|
| Original `BlankOBF.py` (as bundled in v2.03 source) | `73bd45bbbf96aa84a2abf5eef93513126bd3adbbbb5ebd5272776643d99c1fb8` |
| `BlankOBF.py` in this repository (neutered) | `72d0be09a616cd2151c0fea032a2494024909304ead3555490f06a3881d70105` |

Additional reference hashes from the same analysis:

- Source distribution `blankgrabberV2.03-main.zip`: `1b75b915715b86ea70e7015dcae53f06dfc1fa3316551a1416b5b8616fa9e0b4`
- Related payload sample `builder.exe` (Blank Grabber stub, PyInstaller-packed): `8b5eba6961642074384f1fbaa1f936cfbc3a5426df129ca85354243bfde048bb` — reported to URLhaus
- Analysis Links: https://urlhaus.abuse.ch/url/3949909/ https://bazaar.abuse.ch/sample/8b5eba6961642074384f1fbaa1f936cfbc3a5426df129ca85354243bfde048bb/

## Functionality notice

This copy runs and behaves like the original from the outside (same command-line arguments, same silent behavior, same output banner), but every file it produces is non-functional. The nature of the modifications is deliberately not documented here.

Please do not open issues asking to make it work, submit "fixes", or request the original — the original is intentionally not redistributed here in working form. Researchers who need the verbatim artifact for analysis can obtain it from malware sample repositories.

## Credits

Original author: **Blank-c**. The original file header states that the tool may be used in other projects, with or without modifications, provided credit is given — this archive keeps that attribution in the file header. No license claim over the original code is made by this repository; the file is preserved as-found for documentation.

## Disclaimer

Provided as-is for security research, education, and documentation purposes. This repository does not provide working offensive tooling, and none will be provided on request.
