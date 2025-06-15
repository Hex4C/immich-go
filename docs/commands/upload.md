# The **upload** command:
The **upload** command loads photos and videos from the source designated by the sub-command to the Immich server.
**Upload** accepts three sub-commands:
  * [from-folder](subcommands/from-folder.md) to upload photos from a local folder or a zipped archive
  * [from-google-photos](subcommands/from-google-photos.md) to upload photos from a Google Photos takeout archive
  * [from-icloud](subcommands/from-icloud.md) to create a folder archive from an iCloud archive TODO
  * [from-picasa](subcommands/from-picasa.md)  to create a folder archive from a Picasa archive
  * [from-immich](subcommands/from-immich.md) to upload photos from an Immich server to another Immich server

Examples:
```bash
immich-go upload from-folder --server=http://your-ip:2283 --api-key=your-api-key /path/to/your/photos
immich-go upload from-google-photos --server=http://your-ip:2283 --api-key=your-api-key /path/to/your/takeout-*.zip
```


The **upload** command need the following options to manage the connection with the Immich server:


| **Parameter**        | **Default value** | **Description**                                                                                                                           |
| -------------------- | :---------------: | ----------------------------------------------------------------------------------------------------------------------------------------- |
| -s, --server         |                   | Immich server address (e.g http://your-ip:2283 or https://your-domain) (**MANDATORY**)                                                    |
| -k, --api-key        |                   | API Key (**MANDATORY**)                                                                                                                   |
| --admin-api-key      |                   | The Immichs admin's API key, used to pause and resume the server's jobs during operations (**MANDATORY** when uploading for a non-admin ) |
| --no-ui              |      `FALSE`      | Disable the user interface                                                                                                                |
| --api-trace          |      `FALSE`      | Enable trace of api calls                                                                                                                 |
| --client-timeout     |       `20m`       | Set server calls timeout                                                                                                                  |
| --device-uuid string |   `$LOCALHOST`    | Set a device UUID                                                                                                                         |
| --dry-run            |                   | Simulate all server actions                                                                                                               |
| --skip-verify-ssl    |      `FALSE`      | Skip SSL verification                                                                                                                     |
| --time-zone          |                   | Override the system time zone (example: Europe/Paris)                                                                                     |
| --session-tag        |      `FALSE`      | Tag uploaded photos with a tag "{immich-go}/YYYY-MM-DD HH-MM-SS"                                                                          |
| --tag strings        |                   | Add tags to the imported assets. Can be specified multiple times. Hierarchy is supported using a / separator (e.g. 'tag1/subtag1')        |
| --on-server-errors   |      `stop`       | Action to take on server errors, (stop,continue,\<n\> to stop after n errors)                                                             |
| --pause-immich-jobs  |      `TRUE`       | Pause Immich server jobs during the upload process                                                                                        |


## **--client-timeout**
Increase the **--client-timeout** when you have some timeout issues with the server, especialy when uploading large files.

## **--session-tag**
Thanks to the **--session-tag** option, it's easy to identify all photos uploaded during a session, and remove them if needed.
This tag is formatted as `{immich-go}/YYYY-MM-DD HH-MM-SS`. The tag can be deleted without removing the photos.

## **--overwrite**
The `--overwrite` flag ensures that files on the server are always replaced with their local versions during the upload process. If a file does not exist on the server, it will be uploaded as a new file. This option is useful for ensuring that the server always has the latest version of your files.

Example:
```bash
immich-go upload from-folder --server=http://your-ip:2283 --api-key=your-api-key --overwrite /path/to/your/photos
```


