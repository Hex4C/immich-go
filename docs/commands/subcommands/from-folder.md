# **from-folder** sub command:

The **from-folder** sub-command processes a folder tree to upload photos to the Immich server.

| **Parameter**           |           **Default value**           | **Description**                                                                                                                                                                        |
| ----------------------- | :-----------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --ban-file              | [See banned files](#banned-file-list) | Exclude a file based on a pattern (case-insensitive). Can be specified multiple times.                                                                                                 |
| --date-from-name        |                `TRUE`                 | Use the date from the filename if the date isn't available in the metadata (Only for jpg, mp4, heic, dng, cr2, cr3, arw, raf, nef, mov).                                               |
| --date-range            |                                       | Only import photos taken within the specified date range. [See date range possibilities](#date-range)                                                                                  |
| --exclude-extensions    |                                       | Comma-separated list of extension to exclude. (e.g. .gif,.PM)                                                                                                                          |
| --folder-as-album       |                `NONE`                 | Import all files in albums defined by the folder structure. Can be set to 'FOLDER' to use the folder name as the album name, or 'PATH' to use the full path as the album name          |
| --folder-as-tags        |                `FALSE`                | Use the folder structure as tags, (ex: the file  holiday/summer 2024/file.jpg will have the tag holiday/summer 2024)                                                                   |
| --album-path-joiner     |                `" / "`                | Specify a string to use when joining multiple folder names to create an album name (e.g. ' ',' - ')                                                                                    |
| --album-picasa          |                `FALSE`                | Use the Picasa album name found in `.picasa.ini` files                                                                                                                                 |
| --ignore-sidecar-files  |                `FALSE`                | Don't upload sidecar with the photo.                                                                                                                                                   |
| --include-extensions    |                 `all`                 | Comma-separated list of extension to include. (e.g. .jpg,.heic)                                                                                                                        |
| --include-type          |                 `all`                 | Single file type to include. (`VIDEO` or `IMAGE`)                                                                                                                                      |
| --into-album            |                                       | Specify an album to import all files into                                                                                                                                              |
| --manage-burst          |                                       | Manage burst photos. Possible values: NoStack, Stack, StackKeepRaw, StackKeepJPEG.  [See option's details](#burst-detection-and-management)                                            |
| --manage-epson-fastfoto |                `FALSE`                | Manage Epson FastFoto file                                                                                                                                                             |
| --manage-heic-jpeg      |                                       | Manage coupled HEIC and JPEG files. Possible values: NoStack, KeepHeic, KeepJPG, StackCoverHeic, StackCoverJPG.     [See option's details](#management-of-coupled-heic-and-jpeg-files) |
| --manage-raw-jpeg       |                                       | Manage coupled RAW and JPEG files. Possible values: NoStack, KeepRaw, KeepJPG, StackCoverRaw, StackCoverJPG. [See options's details](#management-of-coupled-raw-and-jpeg-files)        |
| --recursive             |                `TRUE`                 | Explore the folder and all its sub-folders                                                                                                                                             |
| --session-tag           |                                       | Tag uploaded photos with a tag "{immich-go}/YYYY-MM-DD HH-MM-SS"                                                                                                                       |
| --tag                   |                                       | Add tags to the imported assets. Can be specified multiple times. Hierarchy is supported using a / separator (e.g. 'tag1/subtag1')                                                     |


## Date of capture

The Immich server takes the date of capture from the metadata of the photo, or in the XMP sidecar file if present.
However, some photos may not have this information.  In this case, Immich-go can infer the date of capture from the filename.

The option `--date-from-name` instructs Immich-go to extract the date of capture from the filename if the date isn't available in the metadata.

Immich-go can extract the date of capture for the following formats: .heic, .heif, .jpg, .jpeg, .dng, .cr2, .mp4, .mov, .cr3..

> Note: `--date-from-name` slows down the process because immich-go needs to parse files to check if the capture date is present in the file.
