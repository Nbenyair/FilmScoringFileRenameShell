# Film Scoring File Rename Shell Script

A macOS shell script designed to automatically rename audio files according to Berklee College of Music's Film Scoring department professional naming conventions. Perfect for streamlining your Pro Tools™ Interchange process when preparing submissions for scoring sessions.

## 🎯 What This Script Does

Transforms audio filenames as they get exported from Cubase™ into clean, professional naming conventions:
- **Input**: `2m04_Violin 1.wav`, `1m12_trumpet_TBR.aiff`, `3m01_synth piano.mp3`
- **Output**: `2m04_STR_vln1.wav`, `1m12_BRS_tpt_TBR.aiff`, `3m01_SYN_synthpiano.mp3`

## ✨ Features

- **Smart Instrument Recognition**: Automatically categorizes 100+ instruments into orchestral and non-orchestral sections
- **Flexible Input**: Handles various naming styles, spaces, uppercase/lowercase
- **Professional Output**: Consistent, Berklee-compliant file naming
- **Conflict Resolution**: Prevents file overwrites with intelligent naming
- **Comprehensive Logging**: Track all changes with timestamped logs
- **macOS Automator Integration**: Right-click contextual menu functionality via native Automator.app

## 🚀 Installation & Setup

### Prerequisites
- **macOS** (tested on macOS 15 - Sequoia)
- **Automator.app** (pre-installed on macOS)
- Basic familiarity with Finder

### Automator Integration Setup
1. Download `FilmScoringFileRenameShellV1.1` from this repository
2. Open macOS **Automator.app**
3. Create a new **Quick Action**
4. Set workflow to receive **"files or folders"** in **Finder**
5. Add the following actions in order:
   - **"New Folder"** action
     - Name: `Auto Film Score Rename`
     - Where: `Same Folder as Input`
   - **"Get Folder Contents"** action
     - Check "Repeat for each subfolder found"
   - **"Run Shell Script"** action
     - Shell: `/bin/bash`
     - Pass input: `as arguments`
     - Copy and paste the entire script content into the text area
6. Save as **"FilmScoringRename"** (or your preferred name)

**Usage**: Select audio files in Finder → Right-click → Quick Actions → FilmScoringRename

> **🛡️ Safety Feature**: This workflow creates a copy of your files in a new folder before renaming, so your original files remain completely safe!

## 📋 How It Works

1. **Select your audio files** in Finder
2. **Right-click → Quick Actions → FilmScoringRename**
3. **New folder created** with your files copied inside
4. **Files are renamed** in the new folder according to Berklee conventions
5. **Automatic log created** showing all changes with timestamps
6. **Completion notification** appears when finished
7. **Original files remain completely safe** in their original location

### What Gets Logged
- Timestamped log file created in the new renamed folder
- Format: `FilmScoring_Rename_Log_YYYYMMDD_HHMMSS.txt`
- Shows: `OriginalFilename --> NewFilename` for each processed file
- Includes start and completion timestamps

## 📋 Requirements

- **OS**: macOS (uses Automator.app)
- **File Types**: `.wav`, `.aiff`, `.mp3`
- **Naming Format**: `CueID_InstrumentName[_TBR|_TBL].ext`

### CueID Format Flexibility
The script handles various CueID naming conventions:
- **Single-digit reel, single-digit cue**: `1m2`, `5m7`
- **Single-digit reel, double-digit cue**: `2m04`, `3m15`
- **Double-digit reel, single-digit cue**: `12m3`, `10m8`
- **Double-digit reel, double-digit cue**: `12m15`, `25m42`

## 🎼 Supported Instruments & Sections

The script recognizes instruments across all major orchestral sections:
- **Strings** (STR): violin, viola, cello, contrabass etc.
- **Woodwinds** (WW): flute, oboe, clarinet, bassoon, etc.
- **Brass** (BRS): trumpet, trombone, French horn, tuba etc.
- **Percussion** (PRC): timpani, snare, cymbals, xylophone, etc.
- **Keyboards & Harp** (KBHRP): piano, organ, celeste, harp
- **Special Categories**: Effects (§), Synths (SYN), Click tracks (CLK)

## 📖 Documentation

- **[Detailed Naming Conventions](NAMING_CONVENTIONS.md)**: Complete technical reference for all supported instruments and naming rules

## ⚠️ Important Notes

- **Complete File Safety**: Creates copies in new folder - original files remain completely untouched
- **Audio Files Only**: Only processes `.wav`, `.aiff`, and `.mp3` files
- **Naming Requirements**: Files must follow `CueID_InstrumentName[_TBR|_TBL].ext` format
- **Unrecognized Instruments**: Files with unknown instrument names get flagged as `CueID_RenameManually!_OriginalName.ext` for manual review
- **Automator Designed**: This script is specifically designed for use with macOS Automator Quick Actions
- **No Backup Needed**: Since originals are preserved, no backup is necessary

## 🎓 Perfect For

- **Berklee Film Scoring Students**: Comply with department standards
- **Professional Composers**: Streamline Pro Tools™ sessions
- **Audio Engineers**: Organize large orchestral projects
- **Anyone**: Working with film scoring audio files

## 📝 Example Transformations

| Input File | Output File | Section |
|------------|-------------|---------|
| `2m04_Violin 1.wav` | `2m04_STR_vln1.wav` | Strings |
| `3m1_violin2.aiff` | `3m1_STR_vln2.aiff` | Strings |
| `12m15_trumpet_TBR.aiff` | `12m15_BRS_tpt_TBR.aiff` | Brass |
| `4m08_Low Brass.wav` | `4m08_BRS_lowbrass.wav` | Brass |
| `2m15_synth pad.mp3` | `2m15_SYN_synthpad.mp3` | Synth |
| `1m05_Reference Mix.wav` | `1m05_MIX_referencemix.wav` | Mix |
| `3m01_reverb.mp3` | `3m01_§_reverb.mp3` | Effects |
| `4m05_click.wav` | `4m05_CLK.wav` | Click Track |
| `5m12_banjo.wav` | `5m12_RenameManually!_banjo.wav` | Unrecognized |

## 🆕 Version 1.1 Features

- ✅ Automatic log generation with timestamps
- ✅ Complete rename tracking and audit trail
- ✅ Enhanced conflict resolution
- ✅ Improved error handling

## 🐛 Support & Contributing

- **Issues**: [GitHub Issues](https://github.com/Nbenyair/FilmScoringFileRenameShell/issues)
- **Email**: nettanettanetta+software@gmail.com
- **Contributing**: Pull requests welcome!

## 📄 License

Open source - feel free to modify and distribute.

---

*Developed for the Berklee College of Music Film Scoring community* 🎬🎵