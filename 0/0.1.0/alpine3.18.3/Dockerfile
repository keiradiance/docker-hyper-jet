FROM alpine:3.18.3

RUN echo -e "https://dl-cdn.alpinelinux.org/alpine/edge/main\nhttps://dl-cdn.alpinelinux.org/alpine/edge/community" \
    >> /etc/apk/repositories

RUN apk update && apk add --no-cache \
    clang=16.0.6-r3 make=4.4.1-r2 cmake=3.27.4-r0 git=2.42.0-r0 pkgconf=2.0.3-r0 \
    libpq-dev=15.4-r0 yaml-dev=0.2.5-r2

RUN git clone --depth 1 https://github.com/intel/safestringlib.git /tmp/lib/safestringlib \
    && cd /tmp/lib/safestringlib \
    && cmake -B build -S . \
    && cd /tmp/lib/safestringlib/build \
    && make -j \
    && make -j install \
    && git clone --depth 1 https://github.com/keiradiance/Collections-C.git /tmp/lib/Collections-C \
    && cd /tmp/lib/Collections-C \
    && cmake -B build -S . \
    && cd /tmp/lib/Collections-C/build \
    && make -j \
    && make -j install \
    && git clone --depth 1 https://github.com/keiradiance/log.c.git /tmp/lib/log.c \
    && cd /tmp/lib/log.c \
    && cmake -B build -S . \
    && cd /tmp/lib/log.c/build \
    && make -j \
    && make -j install \
    && rm -r /tmp/lib
