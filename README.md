# KpqC Test Vectors

Known-answer test (KAT) vectors shared by the KpqC language implementations for
AIMer, HAETAE, NTRU+, and SMAUG-T.

## Overview

The upstream reference implementations distribute their KAT files using
different directory structures and naming conventions. This repository gathers
those files under one predictable layout so that every KpqC implementation can
test against the same data.

Only paths and filenames are normalized. Vector contents, field names, and file
formats are preserved from their upstream sources.

## Available vectors

| Algorithm | Type | Parameter sets | Records |
| --- | --- | --- | ---: |
| AIMer | Signature | `128f`, `128s`, `192f`, `192s`, `256f`, `256s` | 600 |
| HAETAE | Signature | `mode2`, `mode3`, `mode5` | 300 |
| NTRU+ | Key encapsulation | `768`, `864`, `1152` | 300 |
| SMAUG&#8209;T | Key encapsulation | `mode1`, `mode3`, `mode5`, `modet` | 400 |
| **Total** | | **16 parameter sets** | **1,600** |

Each parameter set contains 100 records in a matching file pair:

```text
<algorithm>/<parameter-set>/kat.req
<algorithm>/<parameter-set>/kat.rsp
```

- `kat.req` contains the deterministic test inputs.
- `kat.rsp` contains the corresponding expected outputs.

For example, the AIMer 128f vectors are stored in
`aimer/128f/kat.req` and `aimer/128f/kat.rsp`.

## Using the vectors

Clone this repository next to a KpqC implementation, or configure the
implementation's test suite with an explicit path to this checkout:

```text
workspace/
├── kpqc-test-vectors/
└── kpqc-<language>/
```

The exact test command and path configuration depend on the consuming language
repository. KAT tests should reproduce each operation with the deterministic
input from `kat.req` and compare the result byte-for-byte with `kat.rsp`.

Field names and record formats vary by algorithm. Consumers must parse each
file according to the format used by the corresponding reference
implementation.

For reproducible CI and release testing, pin this repository to a specific
commit or release instead of tracking the default branch.

## Why a separate repository?

The vectors are shared test data rather than language-specific implementation
code. Keeping them in a dedicated repository provides:

- one common source of KAT data for every language implementation;
- consistent paths across algorithms and parameter sets;
- less duplication in package repositories;
- straightforward cross-language conformance and regression testing; and
- clear separation between reference code, test data, and distributed packages.

## Normalization policy

- KAT contents are not modified or reformatted.
- Algorithm-specific fields and formats are preserved.
- Directory names identify the algorithm and parameter set.
- Filenames are standardized as `kat.req` and `kat.rsp`.

## Provenance

The vectors are derived from KAT files distributed by the original algorithm
repositories:

- [AIMer](https://github.com/samsungsds-opensource/AIMer)
- [HAETAE](https://github.com/CryptoLabInc/HAETAE)
- [NTRU+](https://github.com/ntruplus/ntruplus)
- [SMAUG-T](https://github.com/CryptoLabInc/SMAUG-T)

KpqC maintains this repository as a normalized collection of those vectors.
Refer to the original repositories for authoritative implementations,
specifications, and licensing information.
