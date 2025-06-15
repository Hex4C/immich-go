# Immich-Go: Upload Your Photos to Your Immich Server

**Immich-Go** is an open-source tool designed to streamline uploading large photo collections to your self-hosted Immich server.

> ⚠️ This is an early version, not yet extensively tested. Keep a backup copy of your files for safety<br>

## ❤️ Support the project `Immich-go`

* [GitHub Sponsor](https://github.com/sponsors/simulot)
* [PayPal Donation](https://www.paypal.com/donate/?hosted_button_id=VGU2SQE88T2T4)


## 💡 What Makes Immich-Go Special?

* **Simple Installation:** Immich-Go doesn't require NodeJS or Docker, making it easy to get started. It can run on your workstation or a NAS.
* **Upload Your Existing Photo Collection:** Supports uploads from Google Photos Takeouts, iCloud Takeouts, and direct computer folders, preserving metadata like GPS location, capture date, and album information.
* **Handles Large Photo Collections:** Users have successfully uploaded over 100,000 photos from Google Photos Takeouts. It's duplicate-aware and can archive your Immich server content to a folder tree.
* **Has Many Options:** Includes features like stacking burst photos, managing RAW/JPEG and HEIC/JPEG files, and using tags.
* **Runs on Any Platform:** Available for Windows, MacOS, Linux, and FreeBSD.


## 📚 Table of Contents

* **Getting Started**
    * [Installation](docs/installation.md)
    * [Usage](docs/usage.md)
* **Commands**
    * [Archive](docs/commands/archive.md)
    * [Stacking](docs/commands/stacking.md)
    * [Upload](docs/commands/upload.md)
    * **Subcommands**
        * [from-folder](docs/commands/subcommands/from-folder.md)
        * [from-google-photos](docs/commands/subcommands/from-google-photos.md)
        * [from-icould](docs/commands/subcommands/from-icloud.md)
        * [from-immich](docs/commands/subcommands/from-immich.md)
        * [from-picasa](docs/commands/subcommands/from-picasa.md)
* [Examples](docs/examples.md)

## ❤️ Acknowledgments

Kudos to the Immich team for their stunning project! 🤩

This program uses the following 3rd party libraries:
* [https://github.com/rivo/tview](https://github.com/rivo/tview) Terminal User Interface

A big thank you to the project contributors:
* [rodneyosodo](https://github.com/rodneyosodo) GitHub CI, Go linter, and advice
* [sigmahour](https://github.com/sigmahour) SSL management
* [mrwulf](https://github.com/mrwulf) Partner sharing album
* [erkexzcx](https://github.com/erkexzcx) Date determination based on file path and file name
* [benjamonnguyen](https://github.com/benjamonnguyen) Tag API calls
