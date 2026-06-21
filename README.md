# File Classifier / 文件分类工具

[English](README_EN.md)

自动将文件夹中的文件按类型分类移动到对应子文件夹，支持自定义目标文件夹名称。

## 开发背景

我习惯把所有下载的文件都放在同一个文件夹里，时间长了文件越来越多，整理起来很麻烦，于是写了这个工具。

## 使用方法

### 方式一：双击运行

直接双击 `classify.exe`，按提示输入要整理的文件夹路径（支持粘贴路径），回车确认后开始分类。

### 方式二：命令行传入路径

```
classify.exe "D:\Download"
```

## 分类规则

| 类别 | 默认文件夹 | 支持的后缀名 |
|------|-----------|-------------|
| 办公文件 | `1_Files` | `.doc` `.docx` `.xls` `.xlsx` `.xlsm` `.xlsb` `.ppt` `.pptx` `.pps` `.ppsx` `.pot` `.potx` `.odt` `.ods` `.odp` `.rtf` `.csv` `.pdf` `.md` `.txt` |
| 视频 | `2_Videos` | `.mp4` `.avi` `.mkv` `.mov` `.wmv` `.flv` `.webm` `.m4v` `.mpg` `.mpeg` `.3gp` `.3g2` `.ts` `.mts` `.m2ts` `.vob` `.rmvb` `.rm` `.asf` `.divx` `.f4v` `.ogv` |
| 图片 | `3_Images` | `.jpg` `.jpeg` `.png` `.gif` `.bmp` `.webp` `.tiff` `.tif` `.svg` `.ico` `.heic` `.heif` `.raw` `.cr2` `.nef` `.arw` `.dng` `.psd` `.ai` `.eps` |
| 安装文件 | `4_setups` | `.exe` `.whl` |
| 压缩包 | `5_Zips` | `.zip` `.rar` `.7z` `.tar` `.gz` `.bz2` `.xz` `.tgz` `.tbz2` `.lz` `.lzma` `.zst` `.cab` `.iso` `.dmg` |
| 代码文件 | `6_Codes` | `.py` `.pyw` `.ipynb` `.c` `.h` `.cpp` `.cc` `.cxx` `.hpp` `.cs` `.java` `.kt` `.scala` `.dart` `.js` `.ts` `.jsx` `.tsx` `.go` `.rs` `.rb` `.php` `.swift` `.lua` `.sh` `.bat` `.cmd` `.ps1` `.html` `.css` `.scss` `.sql` `.r` `.asm` `.vb` `.mat` `.circ` 等 |
| 音频 | `7_Audios` | `.mp3` `.flac` `.wav` `.aac` `.ogg` `.m4a` `.wma` `.opus` `.ape` `.aiff` `.alac` `.mid` `.midi` `.amr` `.ra` |

不在上述范围内的文件不会被移动。

## 自定义目标文件夹名称

与 `classify.exe` 同目录下的 `folders.txt` 用于配置各类别的目标文件夹名称。

**文件格式**（第一行为说明，从第二行起每行对应一个类别）：

```
第一行是办公文件的目标文件夹，第二行是视频...（说明行，请勿删除）
1_Files
2_Videos
3_Images
4_setups
5_Zips
6_Codes
7_Audios
```

- 如果 `folders.txt` 不存在，程序启动时会自动生成默认配置
- 修改后保存，下次运行即生效
- 目标文件夹若不存在会自动创建；分类完成后若目标文件夹为空则自动删除

## 运行说明

- **同名文件冲突**：目标文件夹中已存在同名文件时，该文件跳过不移动，结束后统一列出
- **文件被占用**：文件正被其他程序使用导致移动失败时，结束后统一列出
- **不处理子文件夹**：只处理目标文件夹根目录下的文件
