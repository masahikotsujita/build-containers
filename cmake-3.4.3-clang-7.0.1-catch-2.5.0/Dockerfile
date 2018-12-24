FROM buildpack-deps:jessie-scm

RUN apt update \
    && apt -qq install -y --no-install-recommends \
    clang \
    make

# Install CMake 3.4.3
ENV PATH $HOME/bin:$PATH
ENV LD_LIBRARY_PATH $HOME/lib/:$LD_LIBRARY_PATH
RUN wget https://cmake.org/files/v3.4/cmake-3.4.3.tar.gz \
    && tar xvfz cmake-3.4.3.tar.gz \
    && cd cmake-3.4.3/ \
    && ./configure --prefix=$HOME \
    && ./bootstrap \
    && make \
    && make install \
    && cmake --version

# Install Clang 7.0.1
RUN svn co http://llvm.org/svn/llvm-project/llvm/tags/RELEASE_701/final llvm \
    && cd llvm/tools \
    && svn co http://llvm.org/svn/llvm-project/cfe/tags/RELEASE_701/final clang \
    && cd ../../ \
    && cd llvm/projects \
    && svn co http://llvm.org/svn/llvm-project/compiler-rt/tags/RELEASE_701/final compiler-rt \
    && cd ../.. \
    && cd llvm/projects \
    && svn co http://llvm.org/svn/llvm-project/libcxx/tags/RELEASE_701/final libcxx \
    && cd ../.. \
    && mkdir build \
    && cd build \
    && cmake -G "Unix Makefiles" \
        -DCMAKE_BUILD_TYPE=Release \
        ../llvm \
    && make \
    && make install \
    && clang --version

# Install Catch2
RUN wget https://github.com/philsquared/Catch/archive/v2.5.0.tar.gz \
    && tar -zxvf v2.5.0.tar.gz \
    && mkdir /usr/local/include/catch2 \
    && cp -rf Catch-2.5.0/include/* /usr/local/include/catch2/
