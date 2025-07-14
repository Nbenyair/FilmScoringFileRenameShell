# Film Scoring File Rename Shell Script (Version 1.1)

## How to Install and Use

### Prerequisites
- macOS (tested on recent versions)
- Basic familiarity with Terminal

### Installation
1. Download or copy the `FilmScoringFileRenameShell` script to a folder on your Mac (e.g., your Desktop).
2. Open Terminal and navigate to the folder containing the script:
   ```sh
   cd ~/Desktop
   ```
3. Make the script executable:
   ```sh
   chmod +x FilmScoringFileRenameShell
   ```

### Usage
1. In Finder, select the audio files you want to rename.
2. Drag and drop them onto the script, or run the script from Terminal with the files as arguments:
   ```sh
   ./FilmScoringFileRenameShell /path/to/files/*.wav
   ```
3. The script will rename the files in place and show a completion message when done.
4. A log file will be automatically created in the same directory as your audio files, showing all original and new names.

### What's New in Version 1.1
- **Automatic Log Generation**: The script now creates a timestamped log file (e.g., `FilmScoring_Rename_Log_20250714_153045.txt`) in the same directory as your audio files
- **Rename Tracking**: The log file shows exactly which files were renamed and their new names in the format: `OriginalName --> NewName`
- **Timestamped Records**: Each log includes start and completion timestamps for your records

### Notes
- Only `.wav`, `.aiff`, and `.mp3` files are processed.
- The script will not overwrite existing files; it will append a unique suffix if needed.
- A pop-up message will appear when renaming is complete.
- Each run creates a unique log file with timestamp to avoid overwriting previous logs.
- The log file will be created in the same directory as your audio files for easy access.

---
