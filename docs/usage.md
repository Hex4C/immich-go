# Immich-Go Usage

This document provides an overview of the commands and sub-commands available in Immich-Go.

The general command usage is:

```bash
immich-go command sub-command options path/to/files
```

## Commands

* [upload](commands/upload.md)
* [archive](commands/archive.md)
* [stack](docs/stack.md)

### General Examples

```bash
## Upload photos from a local folder to your Immich server
immich-go upload from-folder --server=http://your-ip:2283 --api-key=your-api-key /path/to/your/photos

## Archive photos from your Immich server to a local folder
immich-go archive from-immich --from-server=http://your-ip:2283 --from-api-key=your-api-key --write-to-folder=/path/to/archive

## Upload a Google Photos takeout to your Immich server
immich-go upload from-google-photos --server=http://your-ip:2283 --api-key=your-api-key /path/to/your/takeout-*.zip
```


See [examples](examples.md) for additional examples.

## Global Options
The following options are shared by all commands:

| **Parameter**  | **Description**                                       |
| -------------- | ----------------------------------------------------- |
| -h, --help     | Help for Immich-Go                                    |
| -l, --log-file | Write log messages to a file                          |
| --log-level    | Log level (DEBUG\|INFO\|WARN\|ERROR) (default "INFO") |
| --log-type     | Log format (TEXT\|JSON) (default "TEXT")              |
| -v, --version  | Display current version of Immich-Go                  |

**The default path for the log files depend on your system:**

| **OS**  | **Path**                                                           |
| ------- | ------------------------------------------------------------------ |
| Linux   | `$HOME/.cache/immich-go/immich-go_YYYY-MM-DD_HH-MI-SS.log`         |
| Windows | `%LocalAppData%\immich-go\immich-go_YYYY-MM-DD_HH-MI-SS.log`       |
| MacOS   | `$HOME/Library/Caches/immich-go/immich-go_YYYY-MM-DD_HH-MI-SS.log` |

## Environment variables

| **Variable**     | **Description**                                                                                 |
| ---------------- | ----------------------------------------------------------------------------------------------- |
| IMMICHGO_TEMPDIR | Temporary directory used by Immich-go. Default: User's cache folder, or OS temporary directory. |


## Options details

### Burst Detection and Management

The system detects burst photos in the following cases:

| Case                | Description                                                                                                                                                          |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Series of photos    | When the time difference between two photos is less than 900 ms                                                                                                      |
| Huawei smartphones  | Based on file names: <br>- IMG_20231014_183246_BURST001_COVER.jpg<br>- IMG_20231014_183246_BURST002.jpg<br>- IMG_20231014_183246_BURST003.jpg                        |
| Nexus smartphones   | Based on file names:<br>- 00001IMG_00001_BURST20171111030039.jpg<br>-...<br>-00014IMG_00014_BURST20171111030039.jpg<br>-00015IMG_00015_BURST20171111030039_COVER.jpg |
| Pixel smartphones   | Based on file names:<br>- PXL_20230330_184138390.MOTION-01.COVER.jpg<br>- PXL_20230330_184138390.MOTION-02.ORIGINAL.jpg                                              |
| Samsung smartphones | Based on file names:<br>- 20231207_101605_001.jpg<br>- 20231207_101605_002.jpg<br>- 20231207_101605_xxx.jpg                                                          |
| Sony Xperia         | Based on file names:<br>- DSC_0001_BURST20230709220904977.JPG<br>- ...<br>- DSC_0035_BURST20230709220904977_COVER.JPG                                                |
| Nothing Phones      | Based on file names:<br>- 00001IMG_00001_BURST1723801037429_COVER.jpg<br>- 00002IMG_00002_BURST1723801037429.jpg<br>- ...<br>                                        |

The option `--manage-burst` instructs Immich-Go on how to manage burst photos. The following options are available:

| Option          | Description                                                                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `NoStack`       | Do not stack burst photos.                                                                                                                       |
| `Stack`         | Stack all burst photos together. When the cover photo can't be identified with the file name, the first photo of the burst is used as the cover. |
| `StackKeepRaw`  | Stack all burst photos together. Keep only the RAW photos.                                                                                       |
| `StackKeepJPEG` | Stack all burst photos together. Keep only the JPEG photos.                                                                                      |

### Management of Coupled HEIC and JPEG Files

The option `--manage-heic-jpeg` instructs Immich-Go on how to manage coupled HEIC and JPEG files. The following options are available:

| Option           | Description                                                         |
| ---------------- | ------------------------------------------------------------------- |
| `NoStack`        | Do not stack HEIC and JPEG files.                                   |
| `KeepHeic`       | Keep only the HEIC file.                                            |
| `KeepJPG`        | Keep only the JPEG file.                                            |
| `StackCoverHeic` | Stack the HEIC and JPEG files together. The HEIC file is the cover. |
| `StackCoverJPG`  | Stack the HEIC and JPEG files together. The JPEG file is the cover. |

### Management of Coupled RAW and JPEG Files

The option `--manage-raw-jpeg` instructs Immich-Go on how to manage coupled RAW and JPEG files. The following options are available:

| Option          | Description                                                        |
| --------------- | ------------------------------------------------------------------ |
| `NoStack`       | Do not stack RAW and JPEG files.                                   |
| `KeepRaw`       | Keep only the RAW file.                                            |
| `KeepJPG`       | Keep only the JPEG file.                                           |
| `StackCoverRaw` | Stack the RAW and JPEG files together. The RAW file is the cover.  |
| `StackCoverJPG` | Stack the RAW and JPEG files together. The JPEG file is the cover. |

### Management of Epson FastFoto Scanned Photos

This device outputs three files for each scanned photo: the original scan, a "corrected" scan, and the backside of the photo if it has writing on it. The structure looks like this:
- specified-image-name.jpg (Original)
- specified-image-name_a.jpg (Corrected)
- specified-image-name_b.jpg (Back of Photo)

The option `--manage-epson-fastfoto=TRUE` instructs Immich-Go to stack related photos, with the corrected scan as the cover.
