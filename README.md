# Film Scoring File Rename Shell Script

A macOS shell script designed to automatically rename audio files according to Berklee College of Music's Film Scoring department professional naming conventions. Perfect for streamlining your Pro Tools™️ Interchange process when preparing submissions for scoring sessions.

## 🎯 What This Script Does

Transforms messy audio filenames into clean, professional naming conventions:
- **Input**: `2m04_Violin 1.wav`, `1m12_trumpet_TBR.aiff`, `3m01_synth piano.mp3`
- **Output**: `2m04_STR_vln1.wav`, `1m12_BRS_tpt_TBR.aiff`, `3m01_SYN_synthpiano.mp3`

## ✨ Features

- **Smart Instrument Recognition**: Automatically categorizes 100+ instruments into orchestral sections
- **Flexible Input**: Handles various naming styles, spaces, uppercase/lowercase
- **Professional Output**: Consistent, Berklee-compliant file naming
- **Conflict Resolution**: Prevents file overwrites with intelligent naming
- **Comprehensive Logging**: Track all changes with timestamped logs
- **macOS Automator Integration**: Drag-and-drop functionality via Automator.app

## 🚀 Installation & Setup

### Prerequisites
- **macOS** (tested on recent versions)
- **Automator.app** (pre-installed on macOS)
- Basic familiarity with Finder or Terminal

### Option 1: Automator Integration (Recommended)
1. Download `FilmScoringFileRenameShellV1.1` from this repository
2. Open macOS **Automator.app**
3. Create a new **Quick Action**
4. Set workflow to receive **"files or folders"** in **Finder**
5. Add **"Run Shell Script"** action
6. Set **Shell** to `/bin/bash`
7. Set **Pass input** to `as arguments`
8. Copy and paste the entire script content into the text area
9. Save as **"FilmScoringRename"** (or your preferred name)

**Usage**: Select audio files in Finder → Right-click → Quick Actions → FilmScoringRename

### Option 2: Terminal Usage
```bash
# Download script and make executable
chmod +x FilmScoringFileRenameShellV1.1

# Run on files
./FilmScoringFileRenameShellV1.1 *.wav *.aiff *.mp3

# Or drag files onto the script in Finder
./FilmScoringFileRenameShellV1.1 /path/to/your/files/*.wav
```

> **💡 Pro Tip**: The Automator method gives you convenient right-click access directly from Finder!

## 📋 How It Works

1. **Select your audio files** in Finder (or specify in Terminal)
2. **Run the script** via Quick Action or command line
3. **Files are renamed in place** according to Berklee conventions
4. **Automatic log created** showing all changes with timestamps
5. **Completion notification** appears when finished

### What Gets Logged
- Timestamped log file created in same directory as your audio files
- Format: `FilmScoring_Rename_Log_YYYYMMDD_HHMMSS.txt`
- Shows: `OriginalFilename --> NewFilename` for each processed file
- Includes start and completion timestamps

## 📋 Requirements

- **OS**: macOS (uses Automator.app)
- **File Types**: `.wav`, `.aiff`, `.mp3`
- **Naming Format**: `CueID_InstrumentName[_TBR|_TBL].ext`

## 🎼 Supported Instruments & Sections

The script recognizes instruments across all major orchestral sections:
- **Strings** (STR): violin, viola, cello, contrabass
- **Woodwinds** (WW): flute, oboe, clarinet, bassoon, etc.
- **Brass** (BRS): trumpet, trombone, French horn, tuba
- **Percussion** (PRC): timpani, snare, cymbals, xylophone, etc.
- **Keyboards & Harp** (KBHRP): piano, organ, celeste, harp
- **Special Categories**: Effects (§), Synths (SYN), Click tracks (CLK)

## 📖 Documentation

- **[Detailed Naming Conventions](NAMING_CONVENTIONS.md)**: Complete technical reference for all supported instruments and naming rules

## ⚠️ Important Notes

- **File Safety**: Script will not overwrite existing files - adds unique suffix if needed
- **Audio Files Only**: Only processes `.wav`, `.aiff`, and `.mp3` files
- **Naming Requirements**: Files must follow `CueID_InstrumentName[_TBR|_TBL].ext` format
- **In-Place Renaming**: Files are renamed in their current location
- **Backup Recommended**: Always backup important files before batch operations

## 🎓 Perfect For

- **Berklee Film Scoring Students**: Comply with department standards
- **Professional Composers**: Streamline Pro Tools™️ sessions
- **Audio Engineers**: Organize large orchestral projects
- **Anyone**: Working with film scoring audio files

## 📝 Example Transformations

| Input File | Output File | Section |
|------------|-------------|---------|
| `2m04_Violin 1.wav` | `2m04_STR_vln1.wav` | Strings |
| `1m12_trumpet_TBR.aiff` | `1m12_BRS_tpt_TBR.aiff` | Brass |
| `3m01_reverb.mp3` | `3m01_§_reverb.mp3` | Effects |
| `4m05_click.wav` | `4m05_CLK.wav` | Click Track |

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