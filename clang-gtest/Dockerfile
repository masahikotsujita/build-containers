FROM buildpack-deps:jessie-scm

RUN apt update \
    && apt -qq install -y --no-install-recommends \
    clang \
    make \
    cmake

RUN git clone https://github.com/google/googletest.git googletest \
    && cd googletest \
    && mkdir build && cd build \
    && cmake .. \
    && make && make install \
    && cd ../.. && rm -rf googletest

