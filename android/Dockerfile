# Pull base image.
FROM sherylynn/nodejs
MAINTAINER Sherylynn <352281674@qq.com>

# openjdk-8
RUN apk --update add --no-cache openjdk8
ENV JAVA8_HOME /usr/lib/jvm/default-jvm
ENV JAVA_HOME $JAVA8_HOME

#Installs i386 architecture required for running 32 bit Android tools ????
RUN apk --update add --no-cache ncurses5-libs libc6-compat libstdc++ zlib-dev

# ——————————
# Installs Android SDK
# ——————————

ENV ANDROID_SDK_VERSION r24.4.1
ENV ANDROID_SDK_FILENAME android-sdk_${ANDROID_SDK_VERSION}-linux.tgz
ENV ANDROID_SDK_URL http://dl.google.com/android/${ANDROID_SDK_FILENAME}

ENV ANDROID_BUILD_TOOLS_VERSION build-tools-24.0.1,build-tools-24,build-tools-23.0.3,build-tools-23.0.2,build-tools-23.0.1

ENV ANDROID_API_LEVELS android-23
ENV ANDROID_EXTRA_COMPONENTS extra-android-m2repository,extra-google-m2repository
ENV ANDROID_HOME /opt/android-sdk-linux
ENV PATH ${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools
RUN cd /opt && \
    wget -q ${ANDROID_SDK_URL} && \
    tar -xzf ${ANDROID_SDK_FILENAME} && \
    rm ${ANDROID_SDK_FILENAME} && \
    echo y | android update sdk --no-ui -a --filter tools,platform-tools,${ANDROID_API_LEVELS},${ANDROID_BUILD_TOOLS_VERSION} && \
    echo y | android update sdk --no-ui --all --filter "${ANDROID_EXTRA_COMPONENTS}"

# ——————————
# Installs Android NDK
# ——————————

ENV ANDROID_NDK_VERSION r12b
ENV ANDROID_NDK_FILENAME android-ndk-${ANDROID_NDK_VERSION}-linux-x86_64.zip
ENV ANDROID_NDK_URL https://dl.google.com/android/repository/${ANDROID_NDK_FILENAME}
ENV ANDROID_NDK_HOME /opt/android-ndk-${ANDROID_NDK_VERSION}
ENV PATH ${ANDROID_NDK_HOME}:$PATH

RUN cd /opt && \
    wget -q ${ANDROID_NDK_URL} && \
    unzip  ${ANDROID_NDK_FILENAME} && \
    rm ${ANDROID_NDK_FILENAME}


# ——————————
# Installs Gradle
# ——————————

# Gradle
ENV GRADLE_VERSION 2.14

RUN cd /usr/lib \
 && curl -fl https://downloads.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o gradle-bin.zip \
 && unzip "gradle-bin.zip" \
 && ln -s "/usr/lib/gradle-${GRADLE_VERSION}/bin/gradle" /usr/bin/gradle \
 && rm "gradle-bin.zip"

# Set Appropriate Environmental Variables
ENV GRADLE_HOME /usr/lib/gradle
ENV PATH $PATH:$GRADLE_HOME/bin

# ——————————
# Install Basic React-Native packages
# ——————————
RUN npm install react-native-cli -g
RUN npm install rnpm -g
RUN npm install react-native-update-cli -g
ENV LANG en_US.UTF-8