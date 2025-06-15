# Installation

This guide will help you install Immich-Go on your system, whether you prefer using pre-built binaries or building from source.

## Prerequisites

Before you begin, consider the following prerequisites:

* **For Pre-built Binaries:** No additional prerequisites are needed.

* **For Building from Source:**

    * Go 1.23 or higher

    * Git

## Upgrading from the Original `immich-go`, Version 0.22 and Earlier

This version of Immich-Go is a complete rewrite. It's designed for better efficiency, reliability, and ease of use, offering more flexibility and features. Consequently, the command-line options have changed significantly. Please refer to the new documentation for updated options.

Key changes include:

* **Adoption of Linux Convention:** Command-line options now use two dashes for long options (e.g., `--server` instead of `-server`).

* **Restructured CLI Logic:**

    * The `upload` command now has sub-commands (`from-google-photos`, `from-folder`, `from-immich`, etc.) to remove ambiguity.

    * A new `archive` command also uses this sub-command logic, allowing archiving from various sources.

To upgrade, simply install the new version over your previous installation. You can check your current `immich-go` version by running `immich-go --version`.

## Pre-built Binaries

The easiest way to install Immich-Go is by downloading a pre-built binary for your operating system and architecture from the [GitHub releases page](https://github.com/simulot/immich-go/releases).

### Supported Platforms:

* **Operating Systems:** MacOS, Windows, Linux, FreeBSD

* **Architectures:** AMD64 (x86_64), ARM

### Installation Steps (Pre-built)

1.  **Visit the Releases Page:** Go to the [latest releases page](https://github.com/simulot/immich-go/releases/latest).

2.  **Download the Archive:** Download the `.zip` or `.tar.gz` archive appropriate for your system (e.g., `immich-go_Windows_amd64.zip`, `immich-go_Linux_amd64.tar.gz`).

3.  **Extract the Archive:**

    * **For Linux/macOS/FreeBSD:**

        ```bash
        tar -xzf immich-go_*_amd64.tar.gz
        ```

    * **For Windows:** Use your preferred zip tool (like 7-Zip or the built-in Windows extractor) to extract the contents of the archive.

4.  **(Optional) Move to PATH:** To run `immich-go` from any directory in your terminal, move the extracted binary to a directory included in your system's `PATH` environment variable.

    * **Linux/macOS/FreeBSD:**

        ```bash
        sudo mv immich-go /usr/local/bin/
        ```

    * **Windows:** Move `immich-go.exe` to a directory already in your system's `PATH` (e.g., `C:\Windows`, or a custom directory you've added to PATH).

## Building from Source

If pre-built binaries are not available for your specific system or if you prefer to build from source, follow these steps.

### Prerequisites (for building from source)

* Go 1.23 or higher

* Git

### Build Steps

1.  **Clone the Repository:**

    ```bash
    git clone [https://github.com/simulot/immich-go.git](https://github.com/simulot/immich-go.git)
    ```

2.  **Change Directory:** Navigate into the newly cloned project directory.

    ```bash
    cd immich-go
    ```

3.  **Build the Binary:** Compile the source code into an executable binary.

    ```bash
    go build
    ```

4.  **(Optional) Install to GOPATH/bin:**

    ```bash
    go install
    ```

### Building in Termux (for Android)

The pre-built `Linux_Arm64` binaries are generally not compatible with Termux on Android. You will need to build Immich-Go directly within Termux.

1.  **Install Prerequisites:**

    ```bash
    pkg install git golang
    ```

2.  **Follow Build Steps:** Use the same "Build Steps" as described above.

3.  **(Optional) Add GOPATH/bin to PATH:** If you use `go install`, ensure your `GOPATH/bin` directory is in your shell's `PATH` for easy access.

    ```bash
    # Open or create .bashrc (or your shell's equivalent config file)
    nano ~/.bashrc

    # Add the following line
    export PATH=$PATH:$(go env GOPATH)/bin

    # Save and exit (Ctrl+X, then Y, Enter)
    # Apply changes to current session
    source ~/.bashrc
    ```

## Installation with Nix

Immich-Go is packaged with [Nix](https://nixos.org/) and distributed via [nixpkgs](https://search.nixos.org/packages?channel=unstable&type=packages&query=immich-go).

* **Try without Installing (Nix Shell):**

    ```bash
    nix-shell -I "nixpkgs=[https://github.com/NixOS/nixpkgs/archive/nixos-unstable-small.tar.gz](https://github.com/NixOS/nixpkgs/archive/nixos-unstable-small.tar.gz)" -p immich-go
    # Or with flakes enabled
    nix run "github:nixos/nixpkgs?ref=nixos-unstable-small#immich-go" -- --help
    ```

* **Add to System Packages:** You can add `immich-go` to the `environment.systemPackages` section in your `configuration.nix`.

## Verifying the Installation

After installing, confirm that Immich-Go is working correctly by running the version command in your terminal:

```bash
immich-go --version
