# How to run:
#
# $ docker run -it --rm -v $PROJECT_DIR:$VM_DDIR r2dkennobi/android-ci
#
# Note: local.properties can cause a build failure cause of the SDK directory
#       location.
FROM ubuntu:16.04
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"

ENV LANG en_US.UTF-8
RUN apt-get update && apt-get install -y locales && locale-gen $LANG

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get dist-upgrade -y && apt-get install -y \
  software-properties-common \
  build-essential \
  wget \
  gzip \
  curl \
  unzip \
  m4 \
  rsync \
  pkg-config \
  zip \
  zlib1g-dev \
  git \
  --no-install-recommends

# Install Java
RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

# Install Android SDK
ENV SDK_TOOLS_FILE sdk-tools-linux-3859397.zip
RUN wget "https://dl.google.com/android/repository/$SDK_TOOLS_FILE" \
  && unzip "$SDK_TOOLS_FILE" -d /usr/local/android-sdk/ && rm "$SDK_TOOLS_FILE"
RUN yes | /usr/local/android-sdk/tools/bin/sdkmanager --licenses && \
  yes | /usr/local/android-sdk/tools/bin/sdkmanager \
    "platform-tools" \
    "tools" \
    "platforms;android-27" \
    "platforms;android-26" \
    "build-tools;27.0.2" \
    "build-tools;26.0.2" \
    "extras;google;m2repository" \
    "extras;google;google_play_services" \
    "extras;google;m2repository"
ENV ANDROID_HOME /usr/local/android-sdk
ENV PATH $PATH:$ANDROID_SDK_HOME/tools
#ENV JAVA_OPTS "-Xms4096m -Xmx4096"

# Clean up
RUN apt-get autoremove -y \
  && apt-get autoclean -y \
  && rm -rf /var/lib/apt/lists

CMD ["bash"]
