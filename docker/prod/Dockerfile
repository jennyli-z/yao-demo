FROM alpine:latest
ARG VERSION
ARG ARCH
RUN apk --no-cache add curl 
RUN curl -fsSL "https://release-sv.yaoapps.com/archives/yao-${VERSION}-linux-${ARCH}" > /usr/local/bin/yao && \
    chmod +x /usr/local/bin/yao
RUN mkdir -p /data/app && \
    cd /data/app && /usr/local/bin/yao init && \
    cd /data/app && /usr/local/bin/yao migrate && \
    cd /data/app && /usr/local/bin/yao run flows.setmenu && \
    sed -i 's/development/production/g' /data/app/.env
    
VOLUME /data/app
WORKDIR /data/app
EXPOSE 5099
CMD ["/usr/local/bin/yao", "start"]