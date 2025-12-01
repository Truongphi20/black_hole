FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install Ubuntu packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get install -y \
        build-essential \
        git \
        curl \
        pkg-config \
        unzip \
        make \
        wget \
    && apt-get clean

# Install CMake 4.0.2
RUN mkdir -p /usr/local \
    && cd /usr/local \
    && wget https://github.com/Kitware/CMake/releases/download/v4.0.2/cmake-4.0.2-linux-x86_64.sh \
    && chmod +x cmake-4.0.2-linux-x86_64.sh \
    && ./cmake-4.0.2-linux-x86_64.sh --skip-license

# Install vcpkg
RUN git clone https://github.com/microsoft/vcpkg.git /usr/local/vcpkg \
    && /usr/local/vcpkg/bootstrap-vcpkg.sh -disableMetrics

# Add vcpkg to PATH
ENV VCPKG_ROOT=/usr/local/vcpkg
ENV PATH="${VCPKG_ROOT}:${PATH}"

# Default user
USER vscode
