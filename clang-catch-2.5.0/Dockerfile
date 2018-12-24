FROM buildpack-deps:jessie-scm

RUN apt update \
    && apt -qq install -y --no-install-recommends \
    clang \
    make \
    cmake

RUN wget https://github.com/catchorg/Catch2/archive/v2.5.0.tar.gz \
    && tar -zxvf v2.5.0.tar.gz \
    && mkdir /usr/local/include/catch2 \
    && cp -rf Catch2-2.5.0/single_include/catch2/* /usr/local/include/catch2/
