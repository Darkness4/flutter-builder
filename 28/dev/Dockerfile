FROM openjdk:8-jdk-slim

ARG android_compile_sdk=28
ARG android_compile_sdk_latest=28
ARG android_build_tools=29.0.2
ARG android_sdk_tools=4333796
ARG flutter_channel=dev

ENV ANDROID_COMPILE_SDK=$android_compile_sdk
ENV ANDROID_COMPILE_SDK_LATEST=$android_compile_sdk_latest
ENV ANDROID_BUILD_TOOLS=$android_build_tools
ENV ANDROID_SDK_TOOLS=$android_sdk_tools
ENV FLUTTER_CHANNEL=$flutter_channel

ENV ANDROID_HOME="/opt/android-sdk" \
  PATH="/opt/android-sdk/tools/bin:/opt/flutter/bin:/opt/flutter/bin/cache/dart-sdk/bin:$PATH"

RUN apt-get update \
  && apt-get -y install --no-install-recommends curl git lib32stdc++6 unzip \
  && apt-get -y --purge autoremove \
  && apt-get -y autoclean \
  && rm -rf /var/lib/apt/lists/*

RUN git clone -b ${FLUTTER_CHANNEL} https://github.com/flutter/flutter.git /opt/flutter

RUN curl -O https://dl.google.com/android/repository/sdk-tools-linux-${ANDROID_SDK_TOOLS}.zip \
  && mkdir /opt/android-sdk \
  && unzip -qq sdk-tools-linux-${ANDROID_SDK_TOOLS}.zip -d /opt/android-sdk \
  && rm sdk-tools-linux-${ANDROID_SDK_TOOLS}.zip

RUN mkdir ~/.android \
  && echo 'count=0' > ~/.android/repositories.cfg \
  && yes | sdkmanager --licenses \
  && sdkmanager "tools" \
  "platforms;android-${ANDROID_COMPILE_SDK_LATEST}" \
  "build-tools;${ANDROID_BUILD_TOOLS}" \
  "platforms;android-${ANDROID_COMPILE_SDK}" \
  "platform-tools" \
  "extras;android;m2repository" \
  "extras;google;google_play_services" \
  "extras;google;m2repository" > /dev/null \
  && yes | sdkmanager --licenses || echo "Failed" \
  && flutter doctor -v

CMD ["sh"]
