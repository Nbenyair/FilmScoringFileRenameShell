# Film Scoring File Rename Shell Script (Version 1.1)

## Supported Naming Conventions

### Input Filename Format
- The script expects files to be named as:
  
  `CueID_InstrumentName[_TBR|_TBL].ext`
  
  - `CueID`: Any string (e.g., 2m04)
  - `InstrumentName`: Instrument or section name (see below)
  - `_TBR` or `_TBL` (optional): Suffix for Take B Right/Left
  - `.ext`: Supported extensions are `.wav`, `.aiff`, `.mp3`

### Instrument and Section Mapping
- Greedy prefix matching for instrument names (e.g., `vln`, `violin`, `fl`, `flute`, etc.)
- Multi-word and variant names supported (e.g., `Synth Piano`, `Synth Strings`)
- Section keywords anywhere in the name (e.g., `Brass`, `Strings`, `Percussion`, `Winds`, `Mix Bus`)
- Effect tracks: If the instrument name contains effect keywords (e.g., `delay`, `reverb`, `chorus`, etc.), section is set to `§` and the original instrument name is kept
- Any instrument name containing `synth` is assigned section `SYN` and keeps the original instrument name
- Click tracks (`click`, `clk`) are handled as a special case
- Unmapped or ambiguous names are flagged as `RenameManually!`

### Output Filename Format
- Renamed as: `CueID_SECTION_ABBR[Suffix][_TBR|_TBL].ext`
- If a filename conflict occurs, the original instrument name is appended in parentheses

### Version 1.1 Features
- **Automatic Log Generation**: Creates a timestamped log file in the same directory as your audio files
- **Rename Tracking**: Log shows original filename → new filename for each processed file
- **Complete Audit Trail**: Includes start/completion timestamps and log file location

## Bug Reports & Contact
- For bug fixes, feature requests, or questions, please reach out via GitHub issues or email:
  - GitHub: [your-repo-link-here]
  - Email: [your-email-here]

Please include example filenames and a description of the issue when reporting bugs.

---
