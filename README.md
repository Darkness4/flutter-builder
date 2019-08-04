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

## Usage

```sh
docker pull darkness4/flutter-builder:{Android SDK}-{Flutter branch}
```

## Gitlab CI Example

```yaml
# gitlab.yml

image: darkness4/flutter-builder:27

variables:
before_script:
  - flutter channel master
  - flutter upgrade

stages:
  - build

build:
  stage: build
  script:
    - flutter -v build apk --release
    - mv build/app/outputs/apk/app.apk app.apk
  artifacts:
    paths:
      - app.apk
    expire_in: 1 week
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