# File Classifier

[中文](README.md)

Automatically moves files in a folder into categorized subfolders based on file extension. Target folder names are fully customizable.

## Background

I used to dump all my downloaded files into a single folder. Over time it became a mess, so I built this tool to sort everything out automatically.

## Usage

### Option 1: Double-click

Double-click `classify.exe`, enter the path to the folder you want to organize when prompted, then press Enter to confirm and start classifying.

### Option 2: Command line

```
classify.exe "D:\Download"
```

## Classification Rules

| Category | Default Folder | Supported Extensions |
|----------|---------------|----------------------|
| Office files | `1_Files` | `.doc` `.docx` `.xls` `.xlsx` `.xlsm` `.xlsb` `.ppt` `.pptx` `.pps` `.ppsx` `.pot` `.potx` `.odt` `.ods` `.odp` `.rtf` `.csv` `.pdf` `.md` `.txt` |
| Videos | `2_Videos` | `.mp4` `.avi` `.mkv` `.mov` `.wmv` `.flv` `.webm` `.m4v` `.mpg` `.mpeg` `.3gp` `.3g2` `.ts` `.mts` `.m2ts` `.vob` `.rmvb` `.rm` `.asf` `.divx` `.f4v` `.ogv` |
| Images | `3_Images` | `.jpg` `.jpeg` `.png` `.gif` `.bmp` `.webp` `.tiff` `.tif` `.svg` `.ico` `.heic` `.heif` `.raw` `.cr2` `.nef` `.arw` `.dng` `.psd` `.ai` `.eps` |
| Installers | `4_setups` | `.exe` `.whl` |
| Archives | `5_Zips` | `.zip` `.rar` `.7z` `.tar` `.gz` `.bz2` `.xz` `.tgz` `.tbz2` `.lz` `.lzma` `.zst` `.cab` `.iso` `.dmg` |
| Code files | `6_Codes` | `.py` `.pyw` `.ipynb` `.c` `.h` `.cpp` `.cc` `.cxx` `.hpp` `.cs` `.java` `.kt` `.scala` `.dart` `.js` `.ts` `.jsx` `.tsx` `.go` `.rs` `.rb` `.php` `.swift` `.lua` `.sh` `.bat` `.cmd` `.ps1` `.html` `.css` `.scss` `.sql` `.r` `.asm` `.vb` `.mat` `.circ` and more |
| Audio | `7_Audios` | `.mp3` `.flac` `.wav` `.aac` `.ogg` `.m4a` `.wma` `.opus` `.ape` `.aiff` `.alac` `.mid` `.midi` `.amr` `.ra` |

Files with extensions not listed above are left untouched.

## Customizing Target Folder Names

`folders.txt` (located in the same directory as `classify.exe`) controls the name of each target folder.

**File format** — line 1 is a description header, lines 2–8 are the folder names in order:

```
<description line — do not delete>
1_Files
2_Videos
3_Images
4_setups
5_Zips
6_Codes
7_Audios
```

- If `folders.txt` does not exist, it is generated automatically with default names on first run
- Edit and save the file; changes take effect on the next run
- Target folders are created automatically if they do not exist; empty target folders are deleted after classification

## Behavior Notes

- **Filename conflict**: If a file with the same name already exists in the target folder, the file is skipped and listed in a summary at the end
- **File in use**: If a file cannot be moved because it is locked by another process, it is skipped and listed in a summary at the end
- **Subfolders are ignored**: Only files directly in the specified folder are processed
