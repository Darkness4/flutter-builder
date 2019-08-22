# Darkness4/flutter-builder

A flutter-builder container with the choice of the SDK and the flutter channel.

[![pipeline status](https://gitlab.com/Darkness4/flutter-builder/badges/master/pipeline.svg)](https://gitlab.com/Darkness4/flutter-builder/commits/master)
![license](https://img.shields.io/github/license/Darkness4/flutter-builder.svg?style=flat)
![docker build status](https://img.shields.io/docker/automated/darkness4/flutter-builder.svg?style=flat)
![docker pulls](https://img.shields.io/docker/pulls/darkness4/flutter-builder.svg?style=flat)
![docker stars](https://img.shields.io/docker/stars/darkness4/flutter-builder.svg?style=flat)

![docker image size 29-master](https://img.shields.io/microbadger/image-size/darkness4/flutter-builder/29.svg?label=image%20size%20%2829-master%29&style=flat)
![docker image size 28-master](https://img.shields.io/microbadger/image-size/darkness4/flutter-builder/28.svg?label=image%20size%20%2828-master%29&style=flat)
![docker image size 27-master](https://img.shields.io/microbadger/image-size/darkness4/flutter-builder/27.svg?label=image%20size%20%2827-master%29&style=flat)


## Tags

SDK 29

- `latest`, `master`, `latest-master`, `29`, `29-master`
- `dev`, `latest-dev`, `29-dev`
- `beta`, `latest-beta`, `29-beta`
- `stable`, `latest-stable`, `29-stable`

SDK 28

- `28`, `28-master`
- `28-dev`
- `28-beta`
- `28-stable`

SDK 27

- `27`, `27-master`
- `27-dev`
- `27-beta`
- `27-stable`

## Usage

```sh
docker pull darkness4/flutter-builder:{Android SDK}-{Flutter branch}
```

## Gitlab CI Example

```yaml
# gitlab.yml
stages:
  - build

build:
  stage: build
  image: darkness4/flutter-builder:28

  before_script:
    - flutter channel master  # Just to be sure
    - flutter upgrade  # Always update

  script:
    - flutter build apk --target-platform android-arm,android-arm64 --split-per-abi

  after_script:
    - mv build/app/outputs/apk/release/app-armeabi-v7a-release.apk app-armeabi-v7a-release.apk 
    - mv build/app/outputs/apk/release/app-arm64-v8a-release.apk app-arm64-v8a-release.apk 

  artifacts:
    paths:
      - app-armeabi-v7a-release.apk
      - app-arm64-v8a-release.apk
    expire_in: 1 week
```

```

## License

```txt
MIT License

Copyright (c) 2019 Marc NGUYEN

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
