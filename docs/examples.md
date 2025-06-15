# Examples

```bash
## Upload photos from a local folder to your Immich server
immich-go upload from-folder --server=http://your-ip:2283 --api-key=your-api-key /path/to/your/photos

## Archive photos from your Immich server to a local folder
immich-go archive from-immich --from-server=http://your-ip:2283 --from-api-key=your-api-key --write-to-folder=/path/to/archive

## Upload a Google Photos takeout to your Immich server
immich-go upload from-google-photos --server=http://your-ip:2283 --api-key=your-api-key /path/to/your/takeout-*.zip
```


## Additional Examples

#### Importing a Google Takeout with Stacking JPEG and RAW

To import a Google Photos takeout and stack JPEG and RAW files together, with the RAW file as the cover, use the following command:

```bash
immich-go upload from-google-photos --server=http://your-ip:2283 --api-key=your-api-key --manage-raw-jpeg=StackCoverRaw /path/to/your/takeout-*.zip
```

#### Uploading Photos from a Local Folder

To upload photos from a local folder to your Immich server, use the following command:

```bash
immich-go upload from-folder --server=http://your-ip:2283 --api-key=your-api-key /path/to/your/photos
```

#### Archiving Photos from Immich Server

To archive photos from your Immich server to a local folder, use the following command:

```bash
immich-go archive from-immich --server=http://your-ip:2283 --api-key=your-api-key --write-to-folder=/path/to/archive
```

#### Transferring Photos Between Immich Servers

To transfer photos from one Immich server to another, use the following command:

```bash
immich-go upload from-immich --from-server=http://source-ip:2283 --from-api-key=source-api-key --server=http://destination-ip:2283 --api-key=destination-api-key
```

#### Importing Photos with Specific Date Range

To import photos taken within a specific date range from a local folder, use the following command:

```bash
immich-go upload from-folder --server=http://your-ip:2283 --api-key=your-api-key --date-range=2022-01-01,2022-12-31 /path/to/your/photos
```
