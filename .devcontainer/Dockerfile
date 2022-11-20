FROM mcr.microsoft.com/vscode/devcontainers/cpp:debian-10

# Install additional system packages.
RUN apt-get update && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt-get -y install --no-install-recommends python3-pip python3-setuptools libgtk2.0-dev

# Install conan (C/C++ package manager).
RUN pip3 install conan --no-cache-dir

# Add conan remote repository.

# Pre-install all project dependencies using conan.
COPY . /tmp/repo
RUN cd /tmp/repo && conan install ./src --build missing -s build_type=Debug -c tools.system.package_manager:mode=install
