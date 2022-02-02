# json_for_qnimble
A JSON text file for installing qNimble boards to Arduino

The official board manager URL is hosted at https://qnimble.com/package_qnimble_index.json.

Unfortunately, at least on my Windows computer, arm-none-eabi-gcc@9-2019q4 cannot be found.

The problem seems to lie in the `packages` section of the JSON, in the object with name `arm-none-eabi-gcc`. For the system with host `i686-mingw32`, which corresponds to Windows, the URL is broken.

```
{
          "name": "arm-none-eabi-gcc",
          "version": "9-2019q4",
          "systems": [
            {
              "host": "aarch64-linux-gnu",
              "url": "https://developer.arm.com/-/media/Files/downloads/gnu-rm/9-2019q4/gcc-arm-none-eabi-9-2019-q4-major-aarch64-linux.tar.bz2",
              "archiveFileName": "gcc-arm-none-eabi-9-2019-q4-major-aarch64-linux.tar.bz2",
              "checksum": "MD5:0dfa059aae18fcf7d842e30c525076a4",
              "size": "128670769"
            },
            {
              "host": "i686-mingw32",
              "url": "https://github.com/qnimble/arduino_files/releases/download/a8a4aa6/gcc-arm-none-eabi-9-2019-q4-major-win32.zip",
              "archiveFileName": "gcc-arm-none-eabi-9-2019-q4-major-win32.zip",
              "checksum": "SHA-256:2d64567621aa2bb1c7b9ddf36cc40600b8f2a1c7531e3ca5d78bd309a0bc131a",
              "size": "153486619"
            },
            {
              "host": "x86_64-apple-darwin",
              "url": "https://developer.arm.com/-/media/Files/downloads/gnu-rm/9-2019q4/gcc-arm-none-eabi-9-2019-q4-major-mac.tar.bz2",
              "archiveFileName": "gcc-arm-none-eabi-9-2019-q4-major-mac.tar.bz2",
              "checksum": "MD5:241b64f0578db2cf146034fc5bcee3d4",
              "size": "116770520"
            },
            {
              "host": "x86_64-pc-linux-gnu",
              "url": "https://developer.arm.com/-/media/Files/downloads/gnu-rm/9-2019q4/gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2",
              "archiveFileName": "gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2",
              "checksum": "MD5:fe0029de4f4ec43cf7008944e34ff8cc",
              "size": "116802378"
            }
          ]
        }

```

The plan is to replace the URL with the official one hosted by Arm on thier [GNU toolchain website](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads), which is `gcc-arm-none-eabi-9-2019-q4-major-win32.zip`. So the `i686-mingw32` system in `systems` will become:
```
{
              "host": "i686-mingw32",
              "url": "https://developer.arm.com/-/media/Files/downloads/gnu-rm/9-2019q4/gcc-arm-none-eabi-9-2019-q4-major-win32.zip",
              "archiveFileName": "gcc-arm-none-eabi-9-2019-q4-major-win32.zip",
              "checksum": "MD5:82525522fefbde0b7811263ee8172b10",
              "size": "150825950"
            }
```
