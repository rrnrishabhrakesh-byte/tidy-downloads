# File Organizer

A simple Python file organizer for Linux that automatically sorts files into categories such as **Images, Videos, Documents, Audio, Archives, Folders,** and **Others**.

## Features

- Organizes files into category folders
- Supports common image formats
- Supports common video formats
- Supports documents and spreadsheets
- Supports common audio formats
- Supports common archive formats
- Moves folders into a `Folders` directory
- Waits for files to stop changing before moving them
- Watch mode for continuously organizing a folder
- Does not overwrite existing files
- Preview changes before applying them

## Installation

Once the APT repository is available, install it with:

```bash
curl -fsSL https://rrnrishabhrakesh-byte.github.io/file-organizer-apt/public.key \
| sudo gpg --dearmor --yes -o /etc/apt/keyrings/file-organizer-archive-keyring.gpg

echo "deb [signed-by=/etc/apt/keyrings/file-organizer-archive-keyring.gpg] https://rrnrishabhrakesh-byte.github.io/file-organizer-apt stable main" \
| sudo tee /etc/apt/sources.list.d/file-organizer.list > /dev/null

sudo apt update && sudo apt install file-organizer
```

## Usage

By default, the program organizes:

```text
~/Downloads
```

### Preview Changes

Run without `--apply` to see what would happen without moving anything:

```bash
file-organizer
```

### Apply Changes

Actually move the files:

```bash
file-organizer --apply
```

### Organize Another Folder

```bash
file-organizer ~/Desktop --apply
```

### Watch Mode

Continuously check a folder:

```bash
file-organizer --watch --apply
```

By default, the folder is checked every 60 seconds.

### Change the Interval

For example, check every 10 seconds:

```bash
file-organizer --watch --apply --interval 10
```

### Change the Minimum File Age

By default, new files must be at least 30 seconds old before they are moved.

You can change this with:

```bash
file-organizer --apply --min-age 60
```

## Example

Before:

```text
Downloads/
├── photo.jpg
├── video.mp4
├── homework.pdf
├── music.mp3
├── game.zip
└── MyFolder/
```

After:

```text
Downloads/
├── Images/
│   └── photo.jpg
├── Videos/
│   └── video.mp4
├── Documents/
│   └── homework.pdf
├── Audio/
│   └── music.mp3
├── Archives/
│   └── game.zip
└── Folders/
    └── MyFolder/
```

Unknown file types are placed in:

```text
Others/
```

## Safety

The organizer:

- Does not overwrite existing files.
- Skips temporary download files such as `.part` and `.crdownload`.
- Skips files that have been modified recently.
- Runs in preview mode unless `--apply` is specified.

## Command Options

```text
file-organizer [folder] [options]

--apply
    Actually move files.

--watch
    Continuously monitor the folder.

--interval SECONDS
    Time between checks. Default: 60.

--min-age SECONDS
    Minimum age before a file can be moved. Default: 30.

-h, --help
    Show help.
```

## Requirements

- Linux
- Python 3
- Debian/Ubuntu-based distribution when installing through the APT repository

## License

This project is licensed under the MIT License.

See [LICENSE](LICENSE) for more information.

## Author

rrnrishabhrakesh-byte
