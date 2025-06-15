# **from-immich** sub-command:

The sub-command **from-immich** processes an Immich server to upload photos to another Immich server.

| **Parameter**                  | **Default value** | **Description**                                                                      |
| ------------------------------ | :---------------: | ------------------------------------------------------------------------------------ |
| --exclude-extensions           |                   | Comma-separated list of extension to exclude. (e.g. .gif,.PM)                        |
| --from-server                  |                   | Immich server address (e.g http://your-ip:2283 or https://your-domain)               |
| --from-api-key string          |                   | Immich API Key                                                                       |
| --from-album                   |                   | Get assets only from those albums, can be used multiple times                        |
| --from-api-trace               |      `FALSE`      | Enable trace of api calls                                                            |
| --from-client-timeout duration |      `5m0s`       | Set server calls timeout                                                             |
| --from-date-range              |                   | Get assets only within this date range.  [See date range possibilities](#date-range) |
| --from-skip-verify-ssl         |      `FALSE`      | Skip SSL verification                                                                |
| --include-extensions           |       `all`       | Comma-separated list of extension to include. (e.g. .jpg, .heic)                     |
| --include-type                 |       `all`       | Single file type to include. (`VIDEO` or `IMAGE`)                                    |
