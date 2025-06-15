# The **archive** command:

The **archive** command writes the content taken from the source given by the sub-command to a folder tree.
The destination folder isn't wiped out before the operation, so it's possible to add new photos to an existing archive.

The command accepts three sub-commands:
  * [from-folder](subcommands/from-folder.md) to create a folder archive from a local folder or a zipped archive
  * [from-google-photos](subcommands/from-google-photos.md) to create a folder archive from a Google Photos takeout archive
  * [from-icloud](subcommands/from-icloud.md) to create a folder archive from an iCloud archive TODO
  * [from-picasa](subcommands/from-picasa.md)  to create a folder archive from a Picasa archive
  * [from-immich](subcommands/from-immich.md) to create a folder archive from an Immich server

All photos and videos are sorted by date of capture, following this schema: `Folder/YYYY/YYYY-MM/photo.ext`.

Here is an example of what your folder structure might look like:

```
Folder/
├── 2022/
│   ├── 2022-01/
│   │   ├── photo01.jpg
│   │   └── photo01.jpg.JSON
│   ├── 2022-02/
│   │   ├── photo02.jpg
│   │   └── photo02.jpg.JSON
│   └── ...
├── 2023/
│   ├── 2023-03/
│   │   ├── photo03.jpg
│   │   └── photo03.jpg.JSON
│   ├── 2023-04/
│   │   ├── photo04.jpg
│   │   └── photo04.jpg.JSON
│   └── ...
├── 2024/
│   ├── 2024-05/
│   │   ├── photo05.jpg
│   │   └── photo05.jpg.JSON
│   ├── 2024-06/
│   │   ├── photo06.jpg
│   │   └── photo06.jpg.JSON
│   └── ...
```

This structure ensures that photos are neatly organized by year and month within the specified folder, making it easy to locate and manage them.
This folder tree is ready to be archived or migrated to another server.

The general syntax is:

```bash
immich-go archive from-sub-command --write-to-folder=folder options
```
