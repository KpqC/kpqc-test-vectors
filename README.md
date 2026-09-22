# KpqC Test Vectors

Known-answer test (KAT) vectors for the four algorithms selected by the KpqC competition, organized under a consistent layout for reuse across KpqC implementations.

## Overview

The AIMer, HAETAE, NTRU+, and SMAUG-T reference implementations distribute their KAT files using different directory structures and naming conventions.

This repository collects those vectors in one place and normalizes only their paths and filenames. The vector contents are preserved byte-for-byte, including algorithm-specific field names and formats.

## Structure

All vectors follow the same convention:

```text
<algorithm>/<parameter-set>/kat.req
<algorithm>/<parameter-set>/kat.rsp
```

```text
kpqc-test-vectors/
├── aimer/
│   ├── 128f/   ├── kat.req
│   │           └── kat.rsp
│   ├── 128s/
│   ├── 192f/
│   ├── 192s/
│   ├── 256f/
│   └── 256s/
├── haetae/
│   ├── mode2/  ├── kat.req
│   │           └── kat.rsp
│   ├── mode3/
│   └── mode5/
├── ntruplus/
│   ├── 768/    ├── kat.req
│   │           └── kat.rsp
│   ├── 864/
│   └── 1152/
└── smaugt/
    ├── mode1/  ├── kat.req
    │           └── kat.rsp
    ├── mode3/
    ├── mode5/
    └── modet/
```

Every parameter-set directory contains both `kat.req` and `kat.rsp`.

## Why a Separate Repository?

The test vectors are shared test data rather than language-specific implementation code. Keeping them in a dedicated repository provides:

- one common source of KAT data for all language implementations;
- consistent paths across algorithms and parameter sets;
- less duplication across package repositories;
- easier cross-language conformance and regression testing; and
- clear separation between reference code, test data, and language-specific packages.

This allows each language repository to focus on its implementation, bindings, packaging, and platform-specific tests while using the same underlying test vectors.

## Normalization Policy

Only the filesystem layout is normalized.

- KAT contents are not modified or reformatted.
- Algorithm-specific fields and formats are preserved.
- Directory names identify the algorithm and parameter set.
- KAT filenames are standardized as `kat.req` and `kat.rsp`.

Consumers should therefore parse each KAT according to the format used by its corresponding reference implementation.

## Provenance

The vectors are derived from the KAT files distributed with the corresponding KpqC reference implementations. For reproducible testing, use a specific commit or release of this repository.

This is an independent repository and is not an official KpqC repository. Refer to the original KpqC materials and reference implementations for authoritative specifications and licensing information.
