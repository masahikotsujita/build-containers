# Reference:
# https://lindevs.com/install-gcc-on-ubuntu/

# Use Ubuntu 18.04
FROM ubuntu:18.04

# Install GCC11
RUN sudo add-apt-repository -y ppa:ubuntu-toolchain-r/test && \
    sudo apt install -y gcc-11

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