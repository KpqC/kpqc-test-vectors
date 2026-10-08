# KpqC Test Vectors

Known-answer test (KAT) vectors for signature schemes and key encapsulation
mechanisms (KEMs), shared across KpqC implementations.

## Available vectors

| Algorithm | Type | Parameter sets | Records |
| --- | --- | --- | ---: |
| AIMer | Signature | `128f`, `128s`, `192f`, `192s`, `256f`, `256s` | 600 |
| HAETAE | Signature | `mode2`, `mode3`, `mode5` | 300 |
| NTRU+ | KEM | `768`, `864`, `1152` | 300 |
| SMAUG&#8209;T | KEM | `mode1`, `mode3`, `mode5`, `modet` | 400 |
| **Total** | | **16 parameter sets** | **1,600** |

Each parameter set contains 100 records.

## Layout and format

```text
<algorithm>/<parameter-set>/kat.req
<algorithm>/<parameter-set>/kat.rsp
```

- `kat.req` contains deterministic test inputs.
- `kat.rsp` contains the expected outputs.

Only the directory layout and filenames are normalized. File contents, field
names, and formats are preserved from the upstream repositories and may differ
by algorithm.

## Usage

Use this repository as a test fixture and compare generated values byte-for-byte
with the corresponding `kat.rsp` records. Refer to the consuming language
repository for its test command and path configuration.

Pin a commit or release when reproducible test results are required.

## Provenance

The vectors are derived from KAT files distributed by the original algorithm
repositories:

- [AIMer](https://github.com/samsungsds-opensource/AIMer)
- [HAETAE](https://github.com/CryptoLabInc/HAETAE)
- [NTRU+](https://github.com/ntruplus/ntruplus)
- [SMAUG-T](https://github.com/CryptoLabInc/SMAUG-T)

These upstream repositories remain authoritative for specifications,
implementations, and licensing information.
