# Reference:
# https://lindevs.com/install-gcc-on-ubuntu/

# Use Ubuntu 18.04
FROM ubuntu:18.04

# Install Utilities
RUN apt update && apt install -y \
    xz-utils \
    build-essential \
    curl \
    libssl-dev

# Install GCC11
RUN apt update \
    && apt install -y software-properties-common \
    && add-apt-repository -y ppa:ubuntu-toolchain-r/test \
    && apt install -y gcc-11 g++-11

# Set GCC11 as default GCC
RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 20 \
    && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-11 20 \
    && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 10 \
    && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 10

# Install CMake 3.22.3
ENV PATH $HOME/bin:$PATH
ENV LD_LIBRARY_PATH $HOME/lib/:$LD_LIBRARY_PATH
RUN curl -LO https://cmake.org/files/v3.22/cmake-3.22.3.tar.gz \
    && tar xvfz cmake-3.22.3.tar.gz \
    && cd cmake-3.22.3/ \
    && ./configure --prefix=$HOME \
    && ./bootstrap \
    && make \
    && make install \
    && cmake --version

# Install Catch2
RUN curl -LO https://github.com/catchorg/Catch2/releases/download/v2.13.0/catch.hpp \
    && mkdir /usr/local/include/catch2 \
    && cp -rf catch.hpp /usr/local/include/catch2/

# Start from a Bash prompt
CMD [ "/bin/bash" ]