# FFmpeg Static Builds

This repository contains pre-compiled static builds of FFmpeg for various Linux architectures. These builds are sourced from [John Van Sickle's FFmpeg Static Builds](https://johnvansickle.com/ffmpeg/).

## About

FFmpeg is a complete, cross-platform solution to record, convert and stream audio and video. These static builds are self-contained executables that don't require additional libraries to be installed on your system.

## Available Builds

The following FFmpeg release builds (version 7.0.2) are included:

| Architecture | File | Description |
|--------------|------|-------------|
| **amd64** | `ffmpeg-release-amd64-static.tar.xz` | 64-bit Intel/AMD processors |
| **arm64** | `ffmpeg-release-arm64-static.tar.xz` | 64-bit ARM processors (Apple Silicon, modern ARM servers) |
| **armhf** | `ffmpeg-release-armhf-static.tar.xz` | 32-bit ARM with hardware floating point |
| **armel** | `ffmpeg-release-armel-static.tar.xz` | 32-bit ARM with software floating point |
| **i686** | `ffmpeg-release-i686-static.tar.xz` | 32-bit Intel/AMD processors |

## Installation

### 1. Download and Extract

Choose the appropriate build for your system architecture:

```bash
# For 64-bit Intel/AMD systems (most common)
tar -xf ffmpeg-release-amd64-static.tar.xz

# For Apple Silicon Macs or ARM64 servers
tar -xf ffmpeg-release-arm64-static.tar.xz

# For 32-bit ARM with hardware floating point
tar -xf ffmpeg-release-armhf-static.tar.xz

# For 32-bit ARM with software floating point
tar -xf ffmpeg-release-armel-static.tar.xz

# For 32-bit Intel/AMD systems
tar -xf ffmpeg-release-i686-static.tar.xz
```

### 2. Make Executable and Add to PATH

```bash
# Navigate to the extracted directory
cd ffmpeg-*-static

# Make the binaries executable
chmod +x ffmpeg ffprobe

# Copy to a directory in your PATH (optional)
sudo cp ffmpeg ffprobe /usr/local/bin/
```

### 3. Verify Installation

```bash
ffmpeg -version
ffprobe -version
```

## Usage Examples

### Basic Video Conversion
```bash
# Convert MP4 to AVI
ffmpeg -i input.mp4 output.avi

# Convert with specific codec
ffmpeg -i input.mp4 -c:v libx264 -c:a aac output.mp4
```

### Audio Extraction
```bash
# Extract audio from video
ffmpeg -i input.mp4 -vn -acodec copy output.aac
```

### Video Information
```bash
# Get detailed information about a video file
ffprobe -v quiet -print_format json -show_format -show_streams input.mp4
```

### Resize Video
```bash
# Resize video to 720p
ffmpeg -i input.mp4 -vf scale=1280:720 output.mp4
```

## System Requirements

- Linux kernel 3.2.0 or higher
- No additional libraries required (static builds)
- Compatible with most Linux distributions

## License

These FFmpeg builds are licensed under the **GNU General Public License version 3** as provided by the original source.

## Source

These builds are provided by [John Van Sickle](https://johnvansickle.com/ffmpeg/) and are regularly updated. For the latest builds and more information, visit the official site.

## Support

For FFmpeg usage questions and documentation, refer to:
- [Official FFmpeg Documentation](https://ffmpeg.org/documentation.html)
- [FFmpeg Wiki](https://trac.ffmpeg.org/)

For issues with these specific builds, please check [John Van Sickle's site](https://johnvansickle.com/ffmpeg/).

## Architecture Detection

If you're unsure which build to use, you can check your system architecture:

```bash
# Check architecture
uname -m

# Common outputs:
# x86_64    -> use amd64 build
# aarch64   -> use arm64 build  
# armv7l    -> use armhf build
# armv6l    -> use armel build
# i686      -> use i686 build
```
