FROM ubuntu:16.04

ENV SDK_VER_LINK='sdk-tools-linux-3859397'
ENV ANDROID_HOME='/opt/android-sdk-linux'
ENV SDK_TOOL_VER='build-tools;26.0.2 platforms;android-26'
ENV GRADLE_VER='4.7'

RUN apt-get update && \
  apt-get install -y software-properties-common && \
  add-apt-repository -y ppa:webupd8team/java && \
  (echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections) && \
  (echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections) && \
  apt-get update && \
  apt-get install -y oracle-java8-installer \
  wget \
  git \
  curl \
  unzip && \
  apt-get clean && \
  rm -fr /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN wget --quiet https://services.gradle.org/distributions/gradle-${GRADLE_VER}-bin.zip && \
    unzip gradle-${GRADLE_VER}-bin.zip -d /opt/gradle && \
    rm -f gradle-${GRADLE_VER}-bin.zip && \
    ln -s /opt/gradle/gradle-${GRADLE-VER}/bin/gradle /usr/bin

# Install Android SDK
RUN mkdir /opt/android-sdk-linux && \
  wget --quiet https://dl.google.com/android/repository/${SDK_VER_LINK}.zip && \
  unzip ${SDK_VER_LINK}.zip -d /opt/android-sdk-linux && \
  rm -f ${SDK_VER_LINK}.zip && \
  (yes | /opt/android-sdk-linux/tools/bin/sdkmanager ${SDK_TOOL_VER})

CMD ["/bin/bash"]
