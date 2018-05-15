FROM ubuntu:latest
LABEL maintainer="rafaelfgjardim@gmail.com"

ARG NGINX_VERSION=1.14.0
ARG NGINX_RTMP_VERSION=1.2.1

# DEPENDENCIES
RUN apt-get update \
    && apt-get install -y \
        pkg-config \
        git \
        gcc \
        build-essential \
        curl \
        expat \
        musl-dev \
        libc-dev \
        libssl-dev \
        make \
        wget \
        zlib1g-dev \
        libpcre3-dev \
    && apt-get install -f \
    && rm -rf /var/lib/apt/lists/*

RUN cd /tmp/ && \
    wget http://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz && \
    git clone -b v${NGINX_RTMP_VERSION} --depth=1 https://github.com/arut/nginx-rtmp-module.git

RUN cd /tmp && \
    tar xzf nginx-${NGINX_VERSION}.tar.gz && \
    cd nginx-${NGINX_VERSION} && \
    ./configure \
        --prefix=/opt/nginx \
        --with-http_ssl_module \
        --add-module=../nginx-rtmp-module && \
    make && \
    make install

FROM ubuntu:latest 
RUN apt-get update \
    && apt-get install -y \
        openssl \
        ca-certificates \
    && apt-get install -f \
    && rm -rf /var/lib/apt/lists/*

COPY --from=0 /opt/nginx /opt/nginx
COPY --from=0 /tmp/nginx-rtmp-module/stat.xsl /opt/nginx/conf/stat.xsl
RUN rm /opt/nginx/conf/nginx.conf
ADD start.sh /

EXPOSE 1935
EXPOSE 8080

RUN ["chmod", "+x", "start.sh"]
CMD ./start.sh