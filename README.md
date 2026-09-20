# EDC15ORI

Original (stock) ECU firmware archives, organised by make.

Each `ecu_files_<make>/` directory holds one archive (`.zip` / `.rar`) per ECU. The
file name carries the identifying numbers, typically some combination of:

| field | example | notes |
|-------|---------|-------|
| Bosch number   | `0281010215`  | 10 digits, usually starts `0281` (EDC) or `0261` (ME) |
| OEM part number| `038906019AR` | often written spaced: `038 906 019AR` |
| software number| `354 613`     | the "SW" / dataset number, spaced or not |
| model / engine | `1.9 TDI 110` | free text |

`index.tsv` at the repo root is a generated manifest — one `path<TAB>size` line per
archive. Tools should fetch that (~170 KB) rather than cloning the repository (~440 MB);
the identifying numbers are parsed from the path on the client side, so the parser can
improve without regenerating the manifest.

Rebuild it after adding files:

```
cargo run -p edc-core --example ori_index -- build . index.tsv
```

## Layout

```
ecu_files_alfa/        ecu_files_opel/
ecu_files_audi/        ecu_files_peugeot/
ecu_files_bmw/         ecu_files_seat/
ecu_files_citroen/     ecu_files_skoda/
                       ecu_files_volkswagen/
```
