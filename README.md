FFmpeg.wasm Core
================
![FFmpeg.wasm Core](https://github.com/ffmpegwasm/ffmpeg.wasm-core/workflows/FFmpeg.wasm/badge.svg?branch=n4.3.1-wasm)

This is the core part of FFmpeg.wasm where we transpile C/C++ code of FFmpeg to JavaScript/WebAssembly code. It is still very experimental (and slow), but shows the possibilities of using FFmpeg purely in the browser.

If you have any issues for this repository, please put it here: https://github.com/ffmpegwasm/ffmpeg.wasm/issues

## Setup

```
$ git clone https://github.com/ffmpegwasm/ffmpeg.wasm-core
$ git submodule update --init --recursive
```

## Build

1. Use docker (easy way)

Install latest docker and run `build-with-docker.sh`.

```
$ bash build-with-docker.sh
```

2. Install emsdk (unstable way)

Setup the emsdk from [HERE](https://emscripten.org/docs/getting_started/downloads.html) and run `build.sh`.

```
$ bash build.sh
```

If nothing goes wrong, you can find JavaScript files in `wasm/dist`.

## Test

Once the build completes, you can test with following scripts:

```
$ cd wasm
$ npm install
$ npm test
```

## Configuration

#### Base

| Library/Tool Name | Version | Remark |
| ----------------- | ------- | ------ |
| Emscripten | 2.0.8 | |
| FFmpeg | 4.3.1 | |

#### Video

| Library/Tool Name | Version | Remark |
| ----------------- | ------- | ------ |
| x264 | 0.160.x | mp4 format |
| x265 | 3.4 | mp4 format, only works with `-pix_fmt yuv420p10le` and `-pix_fmt yuv420p12le` |
| libvpx | 1.9.0 | webm format |
| theora | 1.1.1 | ogv format |
| aom | 1.0.0 | mkv format, extremely slow (takes over 120s for 1s video), not recommended to use |

#### Audio

| Library/Tool Name | Version | Remark |
| ----------------- | ------- | ------ |
| wavpack | 5.3.0 | wav/wv format |
| lame | 3.100 | mp3 format |
| fdk-aac | 2.0.1 | aac format |
| ogg | 1.3.4 | required by vorbis |
| vorbis | 1.3.6 | ogg format |
