# Reference:
# https://solarianprogrammer.com/2017/12/14/clang-in-docker-container-cpp-17-development/

# Use Ubuntu 18.04
FROM ubuntu:18.04

# Install Clang 10
RUN apt-get update && apt-get install -y \
    xz-utils \
    build-essential \
    curl \
    && rm -rf /var/lib/apt/lists/* \
    && curl -SL https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.0/clang+llvm-10.0.0-x86_64-linux-gnu-ubuntu-18.04.tar.xz \
    | tar -xJC . && \
    mv clang+llvm-10.0.0-x86_64-linux-gnu-ubuntu-18.04 clang_10.0.0 && \
    echo 'export PATH=/clang_10.0.0/bin:$PATH' >> ~/.bashrc && \
    echo 'export LD_LIBRARY_PATH=/clang_10.0.0/lib:$LD_LIBRARY_PATH' >> ~/.bashrc

# Install CMake 3.4.3
ENV PATH $HOME/bin:$PATH
ENV LD_LIBRARY_PATH $HOME/lib/:$LD_LIBRARY_PATH
RUN curl -LO https://cmake.org/files/v3.4/cmake-3.4.3.tar.gz \
    && tar xvfz cmake-3.4.3.tar.gz \
    && cd cmake-3.4.3/ \
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