# The **stack** command:
The stack command open the immich server, for the user associated with the the API-KEY, and stacks related photos together.

The command accepts the following options:

| **Parameter**           | **Default value** | **Description**                                                                                                                                                                     |
| ----------------------- | :---------------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -s, --server            |                   | Immich server address (e.g http://your-ip:2283 or https://your-domain) (**MANDATORY**)                                                                                              |
| -k, --api-key           |                   | API Key (**MANDATORY**)                                                                                                                                                             |
| --api-trace             |      `FALSE`      | Enable trace of api calls                                                                                                                                                           |
| --client-timeout        |      `5m0s`       | Set server calls timeout                                                                                                                                                            |
| --dry-run               |                   | Simulate all server actions...                                                                                                                                                      |
| --skip-verify-ssl       |      `FALSE`      | Skip SSL verification                                                                                                                                                               |
| --time-zone             |                   | Override the system time zone (example: Europe/Paris)                                                                                                                               |
| --manage-burst          |                   | Manage burst photos. Possible values: NoStack, Stack, StackKeepRaw, StackKeepJPEG. [See option's details](#burst-detection-and-management)                                          |
| --manage-epson-fastfoto |      `FALSE`      | Manage Epson FastFoto file                                                                                                                                                          |
| --manage-heic-jpeg      |                   | Manage coupled HEIC and JPEG files. Possible values: NoStack, KeepHeic, KeepJPG, StackCoverHeic, StackCoverJPG   [See option's details](#management-of-coupled-heic-and-jpeg-files) |
| --manage-raw-jpeg       |                   | Manage coupled RAW and JPEG files. Possible values: NoStack, KeepRaw, KeepJPG, StackCoverRaw, StackCoverJPG. [See options's details](#management-of-coupled-raw-and-jpeg-files)     |

