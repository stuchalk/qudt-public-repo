# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project is in the process of adopting [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- New Units
  - `unit:MegaTONNE-PER-YR` by [Jurek Müller](https://github.com/JurekMueller)

### Changed

- Removed the vaem:revision triples that were causing retention of v2.1 strings in the URIs

### Fixed

- Corrected the `qudt:ucumCode` of `unit:TeraW-HR-PER-YR` to "TW.h/a" by [Jurek Müller](https://github.com/JurekMueller)

## [2.1.46] - 2024-12-09

### Added

- QUDT Schema
  - Add the `qudt:altSymbol` property to support using multiple symbols with a unit/quantitykind alongside
    the primary one, which is`qudt:symbol`
- New QuantityKinds
  - `qk:AmountOfSubstanceIonConcentration` as a narrower kind of `qk:Concentration`.
  - `qk:CoefficientOfPerformance` by [lazlop](https://github.com/lazlop)
  - `qk:CompoundPlaneAngle`
  - `qk:CountRate` ( units: `unit:NUM-PER-SEC`, `unit:NUM-PER-HR`, `unit:NUM-PER-YR`)
  - `qk:CurrentOfTheAmountOfSubstance` (replaces`qk:CurrentOfTheAmountOfSubtance`)
  - `qk:RotationalFrequency` (units: `unit:Hz`, `unit:REV-PER-MIN`, `unit:REV-PER-HR`, `unit:REV-PER-SEC`)
  - `qk:VaporPermeability` (unit: `unit:KiloGM-PER-PA-SEC-M`)
  - `qk:VaporPermeance` (for what used to be `qk:VaporPermeability`, see 'Changed')
- New Units
  - `unit:CYC-PER-SEC`
  - `unit:KiloLM`
  - `unit:CD-PER-KiloLM`
  - `unit:CI` (replaces `unit:Ci`)
  - `unit:FLIGHT` (replaces `unit:Flight`)
- Other Additions
  - Add "mph" as `qudt:altSymbol` of `unit:M-PER-HR` from [Toby Broom](https://github.com/Toby-Broom/)
  - Add "kph" as `qudt:altSymbol` of `unit:KiloM-PER-HR` from [Toby Broom](https://github.com/Toby-Broom/)
  - SHACL validation of SHACL shapes by [Dimitris Kontokostas](https://github.com/jimkont)

### Changed

- Enforce at most a single qudt:symbol for all instances.
- Delete spurious qudt:symbol values in a number of quantity kinds
- Correct the conversion offset for MilliDEG_C
- Rename `qk:VaporPermeability` to `qk:VaporPermeance` and change all unit associations accordingly.
- Unify `PER-X` symbols to the 15:1 majority pattern, `"/x"` where `"1/x"` is used
- Unify `NUM-PER-X` symbols to always represent `NUM` as `#` (as has already been used in `unit:NUM`)
- Remove `qk:NumberDensity` from `unit:PER-M3`
- Make `qk:RotationalFrequency` exactMatch of `qk:RotationalVelocity`, remove broader qk
- Make `qk:AngularFrequency` exactMatch of `qk:AngularVelocity`, remove broader qk

### Deprecated

- `unit:Ci` (replaced by: `unit:CI`)
- `unit:Flight` (replaced by: `unit:FLIGHT`)
- `qk:CurrentOfTheAmountOfSubtance` (replaced by `qk:CurrentOfTheAmountOfSubstance`)
- `unit:CFU` (replaced by: `unit:NUM`) - The CFU (colony forming unit) is a context-dependent unit that should
  be part of an ontology with narrower scope than QUDT.

## [2.1.45] - 2024-11-15

### Changed

- Changed the name of the `collections` folder to `validation`.
- Remove all version suffixes from all source files, i.e., `-v2.1.ttl` becomes `.ttl`

### Fixed

- Added `skos:broader` relations to a number of quantity kinds that had none. Note that it is ok for a
  quantity kind to have no broader quantity kind, but these were missing.
- Changed the erroneously used 'qudt:hasDimensionVector' property in `vocab/types/VOCAB_QUDT_DATATYPES-v2.1.ttl`
  file with with a new property qudt:dimensions that denotes the dimensions of a matrix.
- Introduced a maven based build process to automate the manual tasks required for merging PRs and making releases.
  This change does not affect the content of the ontologies.
- Replaced (hopefully) all occurrences of `hr` as a symbol for `unit:HR` with `h`.
- Add `unit:NUM-PER-MilliL`

## 2.1.44 - 2024-10-27

### Fixed

- A new quantity kind, ElevationRelativeToNAP, has been added to support the Amsterdam Ordnance
  System (thanks @RiX012).
- **Big housecleaning month!** Many of the unused graphs that have been lying around the repository
  have been moved to a behind-the-scenes repository, including references to some of the unused
  concepts in our active graphs. If you have been quietly using them yourself in your own work and
  would like us to restore any of them, please let us know in a new Issue. Otherwise, we now have a
  more streamlined repository while retaining all the functionality you have been depending on.
- The qudt:currencyNumber relation now points to a string with the currency code, rather than an
  integer. This makes sense because it is not used for computation - it is a code in the true
  sense. (Thanks for this fix, @fkleedorfer)
- A number of units now point to quantitykind:MassConcentration in addition to MassDensity and Density.
  (thanks @J-meirlaen). (MassDensity and Density are already declared as qudt:exactMatch.
  MassConcentration will be included in these declarations in the future.)

[Unreleased]: https://github.com/qudt/qudt-public-repo/compare/v2.1.46...HEAD
[2.1.46]: https://github.com/qudt/qudt-public-repo/compare/v2.1.45...v2.1.46
[2.1.45]: https://github.com/qudt/qudt-public-repo/compare/v2.1.44...v2.1.45
