# `libvlc` for .NET

This repository is about presenting `libvlc` and its capabilities to .NET developers.
It also contains packaging tools and files for nuget packaging/deployment.
In other words: It's just the same thing as if you had downloaded the files from VideoLAN's website, in a NuGet package,
that you can add in your .NET project so that it gets copied into the output directory.

- [What is libvlc?](#What-is-libvlc)
- [How do I use this thing from .NET?](#How-do-I-use-this-thing-from-.NET)
- [Build and packaging customization with MSBuild](#Build-and-packaging-customization-with-MSBuild)
- [Supported platforms](#Supported-platforms)
  - [Windows Classic](#windows-classic)
  - [Windows Universal](#windows-universal)
  - [Android](#android)
  - [iOS](#iOS)
  - [macOS](#macOS)
  - [tvOS](#tvOS)
  - [Linux](#linux)
- [Roadmap](#roadmap)

# What is libvlc?

`libvlc` is the multimedia framework powering the VLC applications. It is fully opensource, so other apps use it too.

**API documentation**: https://www.videolan.org/developers/vlc/doc/doxygen/html/group__libvlc.html

it contains all modules, data structures and functions documentation to understand how to use the `libvlc` C API.

The **source** is in the main VLC repository: https://github.com/videolan/vlc

`libvlc` is *modularized* into hundreds of plugins, which may be loaded at runtime. This architecture provides great flexibility to developers (both VLC devs and devs consuming the library). The unified, complete and (somewhat) high level `libvlc` C API allows a wide range of operations, such as:
- Network browsing for distant filesystems (SMB, FTP, SFTP, NFS...).
- HDMI passthrough for Audio HD codecs, like E-AC3, TrueHD or DTS-HD.
- Stream to distant renderers, like Chromecast.
- 360 video and 3D audio playback with viewpoint change.
- Support for Ambisonics audio and more than 8 audio channels.
- Subtitles size modification live.
- Hardware decoding and display on all platforms.
- DVD playback and menu navigation.

Full list of features can be found here: https://www.videolan.org/vlc/releases/3.0.0.html

Full directory tree overview of what's included (dlls, headers, lib files) in the nuget can be found at https://github.com/mfkl/libvlc-nuget/blob/master/tree.md

# How do I use this thing from .NET?

There are usually 2 ways to go about consuming C code from .NET:
- Using [C++/CX](https://docs.microsoft.com/en-us/cpp/cppcx/visual-c-language-reference-c-cx). This allows to author [Windows Runtime components](https://docs.microsoft.com/en-us/cpp/windows/windows-runtime-cpp-template-library-wrl) and it is Windows-specific. [VLC for UWP](https://code.videolan.org/videolan/vlc-winrt) currrently works this way using both [libvlcppcx](https://github.com/kakone/libVLCX) and [libvlcpp](https://code.videolan.org/videolan/libvlcpp).
- Using [P/Invoke](http://www.mono-project.com/docs/advanced/pinvoke/). If crossplatform is a focus, you should checkout [LibVLCSharp](https://github.com/videolan/libvlcsharp).

Versioning of the nuget packages naturally follow the libvlc versioning.

# Build and packaging customization with MSBuild

How do I configure what gets copied to my output directory?

Currently, you can customize three things during the build:

- [Whether the library gets copied or not](library-copy-enabling.md)
- [Where the library is placed in the output folder](files-location-selection.md)
- [Which files are copied](cherry-picking.md)

# Supported platforms

#### LibVLC 3:

Latest stable version is [3.0.7.1](https://github.com/videolan/vlc-3.0/releases/tag/3.0.7.1). Feel free to check out the [release notes](https://github.com/videolan/vlc-3.0/blob/master/NEWS).

Minimum OS version supported by LibVLC 3.x:

- Windows XP
- macOS 10.7
- iOS 7
- Android 2.3

## Windows Classic

```cmd
 dotnet add package VideoLAN.LibVLC.Windows
```

[![NuGet version](https://img.shields.io/nuget/v/VideoLAN.LibVLC.Windows.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.Windows)
[![NuGet downloads](https://img.shields.io/nuget/dt/VideoLAN.LibVLC.Windows.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.Windows)

#### Supported CPU architectures:

- x86
- x64

*Note: if you intend to use libvlc with UWP projects, you probably need to install the [UWP](#windows-universal) package instead because this build directly uses win32 APIs.*

## Windows Universal

```cmd
 dotnet add package VideoLAN.LibVLC.UWP
```

[![NuGet version](https://img.shields.io/nuget/v/VideoLAN.LibVLC.UWP.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.UWP)
[![NuGet downloads](https://img.shields.io/nuget/dt/VideoLAN.LibVLC.UWP.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.UWP)

#### Supported CPU architectures:

- x86
- x64
- ARM

## Android

```cmd
dotnet add package VideoLAN.LibVLC.Android
```

[![NuGet Stats](https://img.shields.io/nuget/v/VideoLAN.LibVLC.Android.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.Android)
[![NuGet Stats](https://img.shields.io/nuget/dt/VideoLAN.LibVLC.Android.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.Android)

#### Supported CPU architectures:

- armeabi-v7a
- arm64-v8a
- x86
- x86_64

## iOS

```cmd
dotnet add package VideoLAN.LibVLC.iOS --version 3.1.5-alpha
```

[![NuGet Stats](https://img.shields.io/nuget/v/VideoLAN.LibVLC.iOS.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.iOS)
[![NuGet Stats](https://img.shields.io/nuget/dt/VideoLAN.LibVLC.iOS.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.iOS)

#### Supported CPU architectures:

- i386
- x86_64
- ARMv7
- ARM64

## macOS

```cmd
dotnet add package VideoLAN.LibVLC.Mac
```

[![NuGet Stats](https://img.shields.io/nuget/v/VideoLAN.LibVLC.Mac.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.Mac)
[![NuGet Stats](https://img.shields.io/nuget/dt/VideoLAN.LibVLC.Mac.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.Mac)

#### Supported CPU architecture:

- x86_64

## tvOS

```cmd
 dotnet add package VideoLAN.LibVLC.tvOS --version 3.2.0-alpha 
```

[![NuGet Stats](https://img.shields.io/nuget/v/VideoLAN.LibVLC.tvOS.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.tvOS)
[![NuGet Stats](https://img.shields.io/nuget/dt/VideoLAN.LibVLC.tvOS.svg)](https://www.nuget.org/packages/VideoLAN.LibVLC.tvOS)

#### Supported CPU architecture:

- x86_64
- ARM64

## Linux

For Ubuntu, follow this [guide](https://code.videolan.org/videolan/LibVLCSharp/blob/master/docs/linux-setup.md).

# Roadmap

- Unity and other game engines
- WebAssembly
- Tizen?
