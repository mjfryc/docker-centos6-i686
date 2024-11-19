FROM mjfryc/centos6-i686-development:v1

RUN mkdir -p /root/docker_build_tmp
COPY devtoolset-4-centos6-i386-0.1_oc20170208-1.2.i686.rpm /root/docker_build_tmp
COPY cmake-3.31.0.tar.gz /root/docker_build_tmp
COPY openssl-3.4.0.tar.gz /root/docker_build_tmp

# Reference: https://software.opensuse.org//download.html?project=isv%3AownCloud%3Adesktop%3Aclient-2.4.1&package=devtoolset-4-centos6-i386
RUN linux32 yum -y localinstall /root/docker_build_tmp/devtoolset-4-centos6-i386-0.1_oc20170208-1.2.i686.rpm

# Source: https://github.com/openssl/openssl/releases/download/openssl-3.4.0/openssl-3.4.0.tar.gz
RUN linux32 /bin/bash -c "cd /root/docker_build_tmp && tar -xf 'openssl-3.4.0.tar.gz' && cd 'openssl-3.4.0' && ./Configure && make && make -j$(nproc) install;"

# Source: https://cmake.org/download/
# Source: https://github.com/Kitware/CMake/releases/download/v3.31.0/cmake-3.31.0.tar.gz
# Reference: https://gitlab.kitware.com/cmake/cmake - "Building CMake from Scratch"
RUN linux32 /bin/bash -c "source /opt/rh/devtoolset-4/enable && cd /root/docker_build_tmp && tar -xf cmake-3.31.0.tar.gz && cd cmake-3.31.0 && ./bootstrap && make -j$(nproc) && echo '### make test skipped ###' && make install;"

RUN rm -rf /root/docker_build_tmp

