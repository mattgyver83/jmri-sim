FROM eclipse-temurin:17-jre-jammy

ARG JMRI_VERSION=5.16
ARG JMRI_BUILD=R909e15189e

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \
        ca-certificates \
        tar \
        gzip && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /opt

RUN curl -fL \
    "https://github.com/JMRI/JMRI/releases/download/v${JMRI_VERSION}/JMRI.${JMRI_VERSION}+${JMRI_BUILD}.tgz" \
    -o jmri.tgz && \
    tar -xzf jmri.tgz && \
    rm jmri.tgz

RUN useradd -m -u 1000 jmri

USER jmri
WORKDIR /home/jmri

ENV JAVA_TOOL_OPTIONS="-Djava.awt.headless=true"

EXPOSE 12080

CMD ["/opt/JMRI/JmriFaceless"]
