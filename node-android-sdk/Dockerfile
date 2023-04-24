FROM androidsdk/android-31 AS builder

FROM gradle:7-jdk11

WORKDIR /app

COPY --from=builder /opt/android-sdk-linux /opt/android-sdk-linux

ENV ANDROID_HOME /opt/android-sdk-linux
ENV PATH ${PATH}:${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/platform-tools:${ANDROID_HOME}/tools}

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        curl \
    && curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \