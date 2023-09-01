FROM alpine:3.18.3

RUN echo -e "https://dl-cdn.alpinelinux.org/alpine/edge/main\nhttps://dl-cdn.alpinelinux.org/alpine/edge/community" \
    >> /etc/apk/repositories

RUN apk update && apk add --no-cache \
    clang=16.0.6-r3 make=4.4.1-r2 cmake=3.27.4-r0 git=2.42.0-r0 \
    yaml-dev=0.2.5-r2

RUN git clone --depth 1 https://github.com/intel/safestringlib.git /opt/safestringlib \
    && cd /opt/safestringlib \
    && cmake -S . -B build \
    && cd /opt/safestringlib/build \
    && make -j \
    && make -j install \
    && rm -r /opt/safestringlib
