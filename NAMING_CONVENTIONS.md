# Naming Conventions - Technical Reference

This document provides the complete technical specification for the Film Scoring File Rename Shell Script's naming conventions and instrument mappings.

## Supported Naming Conventions

### Input Filename Format
- The script expects files to be named as:
  
  `CueID_InstrumentName[_TBR|_TBL].ext`
  
  - `CueID`: Any string following reel/cue format (e.g., 2m04, 12m15, 3m1)
    - Supports 1-2 digit reel numbers and 1-2 digit cue numbers
    - Examples: `1m2`, `2m04`, `12m3`, `25m42`
  - `InstrumentName`: Instrument or section name (see below)
  - `_TBR` or `_TBL` (optional): Suffix for Take B Right/Left (case-insensitive)
  - `.ext`: Supported extensions are `.wav`, `.aiff`, `.mp3` (case-insensitive)

### File Processing Requirements
- **Audio files only**: Non-audio files are automatically skipped
- **Exact format required**: Filenames must contain exactly one underscore (excluding `_TBR`/`_TBL`)
- **Invalid formats skipped**: Files not matching the expected pattern are ignored
- **Duplicate protection**: Uses `mv -n` to prevent overwriting existing files
- **Safe processing**: When used with Automator workflow, creates copies before renaming

### Instrument and Section Mapping
- **Greedy prefix matching**: Longest matching prefix wins (e.g., `vln`, `violin`, `fl`, `flute`, etc.)
- **Multi-word names supported**: Spaces are normalized during matching (e.g., `Synth Piano`, `Synth Strings`)
- **Section keywords**: If no prefix match is found, checks for section keywords anywhere in the name:
  - `brass`, `brs` → BRS section
  - `winds`, `ww`, `woodwinds` → WW section  
  - `strings`, `str` → STR section
  - `percussion`, `prc`, `perc` → PRC section
  - `mixbus`, `mix bus` → MIX section
- **Effect tracks**: If instrument name contains effect keywords (`delay`, `reverb`, `chorus`, `eq`, `fx`, etc.), section is set to `§` and the original instrument name is preserved
- **Synth instruments**: Any instrument name containing `synth` is assigned section `SYN` and keeps the original instrument name
- **Click tracks**: `click` or `clk` are handled specially - renamed to `CueID_CLK` with no section prefix
- **Case insensitive**: All matching is case-insensitive
- **Unmapped instruments**: Names that don't match any pattern are flagged as `RenameManually!`

### Output Filename Format
- Renamed as: `CueID_SECTION_ABBR[Suffix][_TBR|_TBL].ext`
  - For **effect tracks**: `CueID_§_OriginalInstrumentName[_TBR|_TBL].ext`
  - For **synth instruments**: `CueID_SYN_OriginalInstrumentName[_TBR|_TBL].ext`
  - For **click tracks**: `CueID_CLK.ext` (no section prefix)
  - For **unmapped instruments**: `CueID_RenameManually!_OriginalInstrumentName[_TBR|_TBL].ext`
- If a filename conflict occurs, the original instrument name is appended in parentheses: `(OriginalInstrument)`
- For multiple conflicts, a counter is added: `(OriginalInstrument_2)`, `(OriginalInstrument_3)`, etc.

### Version 1.1 Features
- **Automatic Log Generation**: Creates a timestamped log file in the renamed folder
- **Rename Tracking**: Log shows original filename → new filename for each processed file
- **Complete Audit Trail**: Includes start/completion timestamps and log file location

## Examples

### Standard Instrument Mapping
- `2m04_Violin 1.wav` → `2m04_STR_vln1.wav`
- `4m05_violin2.wav` → `4m05_STR_vln2.wav`
- `1m12_trumpet_TBR.aiff` → `1m12_BRS_tpt_TBR.aiff`
- `3m01_flute.mp3` → `3m01_WW_fl.mp3`

### Section Keywords
- `2m04_strings.wav` → `2m04_STR_str.wav`
- `1m12_brass.aiff` → `1m12_BRS_brs.aiff`
- `3m01_woodwinds.mp3` → `3m01_WW_ww.mp3`

### Special Cases
- `2m04_click.wav` → `2m04_CLK.wav` (no section)
- `1m12_synth piano.aiff` → `1m12_SYN_synthpiano.aiff`
- `3m01_reverb.mp3` → `3m01_§_reverb.mp3`
- `4m05_guitar.wav` → `4m05_RenameManually!_guitar.wav` (unmapped)

### Conflict Resolution
- If `2m04_STR_vln.wav` already exists:
  - `2m04_violin.wav` → `2m04_STR_vln(violin).wav`
- If that also exists:
  - Next file → `2m04_STR_vln(violin_2).wav`

## Bug Reports & Contact
- For bug fixes, feature requests, or questions, please reach out via GitHub issues or email:
- **Issues**: [GitHub Issues](https://github.com/Nbenyair/FilmScoringFileRenameShell/issues)
- **Email**: nettanettanetta+software@gmail.com

Please include example filenames and a description of the issue when reporting bugs.