FROM ubuntu:20.04
ARG VERSION
ARG ARCH
RUN groupadd -r yao && useradd -r -g yao yao && \
    apt-get update && \
    apt-get install -y curl sudo procps net-tools
RUN curl -fsSL "https://release-sv.yaoapps.com/archives/yao-${VERSION}-linux-${ARCH}" > /usr/local/bin/yao && \
    chmod +x /usr/local/bin/yao && \
    mkdir -p /data/app

VOLUME /data/app
WORKDIR /data/app
EXPOSE 5099
CMD ["tail", "-f","/dev/null"]