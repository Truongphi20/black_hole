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
        # --- OpenGL + X11 dependencies for GLEW + GLFW ---
        libx11-dev \
        libxrandr-dev \
        libxinerama-dev \
        libxcursor-dev \
        libxi-dev \
        xorg-dev \
        libgl1-mesa-dev \
        libglu1-mesa-dev \
    && apt-get clean

# Install CMake 4.0.2
RUN mkdir -p /usr/local \
    && cd /usr/local \
    && wget https://github.com/Kitware/CMake/releases/download/v4.0.2/cmake-4.0.2-linux-x86_64.sh \
    && chmod +x cmake-4.0.2-linux-x86_64.sh \
    && ./cmake-4.0.2-linux-x86_64.sh --skip-license

# Switch to vscode temporarily for installing vcpkg
USER vscode

RUN git clone https://github.com/microsoft/vcpkg.git /home/vscode/vcpkg \
    && /home/vscode/vcpkg/bootstrap-vcpkg.sh -disableMetrics

ENV VCPKG_ROOT=/home/vscode/vcpkg
ENV PATH="${VCPKG_ROOT}:${PATH}"
