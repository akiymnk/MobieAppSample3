FROM mcr.microsoft.com/devcontainers/universal:2


ENV ANDROID_SDK_HOME /opt/android-sdk-linux
ENV ANDROID_SDK_ROOT /opt/android-sdk-linux
ENV ANDROID_HOME /opt/android-sdk-linux
ENV ANDROID_SDK /opt/android-sdk-linux

ENV DEBIAN_FRONTEND noninteractive

# Install required tools
# Dependencies to execute Android builds
RUN dpkg --add-architecture i386

RUN apt-get update -yqq
RUN apt-get install -y \
  curl \
  expect \
  git \
  make \
  openjdk-17-jdk \
  wget \
  unzip \
  vim \
  openssh-client \
  locales \
  libarchive-tools \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8  
#RUN localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8

ENV LANG ja_JP.UTF-8

RUN groupadd android && useradd -d /opt/android-sdk-linux -g android -u 1001 android

COPY tools /opt/tools

COPY licenses /opt/licenses

WORKDIR /opt/android-sdk-linux

RUN /opt/tools/entrypoint.sh built-in


RUN npm install --global @expo/ngrok@^4.1.0
RUN npm install --global expo
RUN npm install -g eas-cli
