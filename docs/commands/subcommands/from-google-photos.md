# **From-google-photos** sub command:


The **from-google-photos** sub-command processes a Google Photos takeout archive to upload photos to the Immich server.

| **Parameter**             |           **Default value**           | **Description**                                                                                                                                                                    |
| ------------------------- | :-----------------------------------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --ban-file FileList       | [See banned files](#banned-file-list) | Exclude a file based on a pattern (case-insensitive). Can be specified multiple times.                                                                                             |
| --date-range              |                                       | Only import photos taken within the specified date range [See date range possibilities](#date-range)                                                                               |
| --exclude-extensions      |                                       | Comma-separated list of extension to exclude. (e.g. .gif, .PM)                                                                                                                     |
| --from-album-name string  |                                       | Only import photos from the specified Google Photos album                                                                                                                          |
| -a, --include-archived    |                `TRUE`                 | Import archived Google Photos                                                                                                                                                      |
| --include-extensions      |                 `all`                 | Comma-separated list of extension to include. (e.g. .jpg, .heic)                                                                                                                   |
| --include-type            |                 `all`                 | Single file type to include. (`VIDEO` or `IMAGE`)                                                                                                                                  |
| -p, --include-partner     |                `TRUE`                 | Import photos from your partner's Google Photos account                                                                                                                            |
| -t, --include-trashed     |                `FALSE`                | Import photos that are marked as trashed in Google Photos                                                                                                                          |
| -u, --include-unmatched   |                `FALSE`                | Import photos that do not have a matching JSON file in the takeout                                                                                                                 |
| --include-untitled-albums |                `FALSE`                | Include photos from albums without a title in the import process                                                                                                                   |
| --manage-burst            |                                       | Manage burst photos. Possible values: NoStack, Stack, StackKeepRaw, StackKeepJPEG. [See option's details](#burst-detection-and-management)                                         |
| --manage-epson-fastfoto   |                `FALSE`                | Manage Epson FastFoto file (default: false)                                                                                                                                        |
| --manage-heic-jpeg        |                                       | Manage coupled HEIC and JPEG files. Possible values: NoStack, KeepHeic, KeepJPG, StackCoverHeic, StackCoverJPG. [See option's details](#management-of-coupled-heic-and-jpeg-files) |
| --manage-raw-jpeg         |                                       | Manage coupled RAW and JPEG files. Possible values: NoStack, KeepRaw, KeepJPG, StackCoverRaw, StackCoverJPG. [See options's details](#management-of-coupled-raw-and-jpeg-files)    |
| --partner-shared-album    |                                       | Add partner's photo to the specified album name                                                                                                                                    |
| --session-tag             |                `FALSE`                | Tag uploaded photos with a tag "{immich-go}/YYYY-MM-DD HH-MM-SS"                                                                                                                   |
| --sync-albums             |                `TRUE`                 | Automatically create albums in Immich that match the albums in your Google Photos takeout                                                                                          |
| --tag strings             |                                       | Add tags to the imported assets. Can be specified multiple times. Hierarchy is supported using a / separator (e.g. 'tag1/subtag1')                                                 |
| --takeout-tag             |                `TRUE`                 | Tag uploaded photos with a tag "{takeout}/takeout-YYYYMMDDTHHMMSSZ"                                                                                                                |
| --people-tag              |                `TRUE`                 | Tag uploaded photos with tags \"people/name\" found in the JSON file                                                                                                               |

## Google Photos Best Practices:

* **Taking Out Your Photos:**
  * Choose the ZIP format when creating your takeout for easier import.
  * Select the largest file size available (50GB) to minimize the number of archive parts.
  * Download all parts to your computer.

* **Importing Your Photos:**
  * If your takeout is in ZIP format, you can import it directly without needing to unzip the files first.
  * It's important to import all parts of the takeout together, as some data might be spread across multiple files. Use `/path/to/your/files/takeout-*.zip` as the file name.
  * For **.tgz** files (compressed tar archives), you'll need to decompress all the files into a single folder before importing. Then use the command `immich-go upload from-google-photos /path/to/your/files`.  
  * You can remove any unwanted files or folders from your takeout before importing.
  * Restarting an interrupted import won't cause any problems and will resume where it left off.

* **What if many of my files are not imported?**
  * Verify if all takeout parts have been included in the processing. Have you used the `takeout-*.zip` file name pattern?
  * Sometimes, the takeout result is incomplete. Request another takeout, either for an entire year or in smaller increments.
  * Force the import of files despite missing JSON files using the option `--include-unmatched`.

## Takeout Tag

Immich-Go can tag all imported photos with a takeout tag. The tag is formatted as `{takeout}/takeout-YYYYMMDDTHHMMSSZ`. This tag can be used to identify all photos imported from a Google Photos takeout, making it easy to remove them if needed.
