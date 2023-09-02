FROM alpine:3.18.3

RUN echo -e "https://dl-cdn.alpinelinux.org/alpine/edge/main\nhttps://dl-cdn.alpinelinux.org/alpine/edge/community" \
    >> /etc/apk/repositories

RUN apk update && apk add --no-cache \
    clang=16.0.6-r3 make=4.4.1-r2 cmake=3.27.4-r0 git=2.42.0-r0 \
    yaml-dev=0.2.5-r2

RUN git clone --depth 1 https://github.com/intel/safestringlib.git /tmp/safestringlib \
    && cd /tmp/safestringlib \
    && cmake -B build -S . \
    && cd /tmp/safestringlib/build \
    && make -j \
    && make -j install \
    && rm -r /tmp/safestringlib

RUN git clone --depth 1 https://github.com/keiradiance/libdict.git /tmp/libdict \
    && cd /tmp/libdict \
    && cmake -B build -S . \
    && cd /tmp/libdict/build \
    && make -j \
    && make -j install \
    && rm -r /tmp/libdict

RUN git clone --depth 1 https://github.com/keiradiance/log.c.git /tmp/log.c \
    && cd /tmp/log.c \
    && cmake -B build -S . \
    && cd /tmp/log.c/build \
    && make -j \
    && make -j install \
    && rm -r /tmp/log.c
