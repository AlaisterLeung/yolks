#
# Copyright (c) 2021 Matthew Penner
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

FROM        --platform=$TARGETOS/$TARGETARCH node:14-bullseye-slim

LABEL       author="Matthew Penner" maintainer="matthew@pterodactyl.io"

LABEL       org.opencontainers.image.source="https://github.com/pterodactyl/yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN         apt update -y \
 			&& apt install -y curl wget ca-certificates openssl git tar zip unzip sqlite3 libsqlite3-dev python3 python3-dev fontconfig libfreetype6 tzdata iproute2 libstdc++6 ffmpeg dnsutils build-essential libtool pkg-config \
 			&& npm install -g npm \
 			&& npm uninstall -g yarn pnpm \
 			&& npm install -g corepack --force \
			&& npm config set python python3 \
 			&& useradd -d /home/container -m container \
			&& CODE_VERSION="$(curl -fsSLI -o /dev/null -w "%{url_effective}" https://github.com/coder/code-server/releases/latest)" \
			&& CODE_VERSION="${CODE_VERSION#https://github.com/coder/code-server/releases/tag/v}" \
			&& mkdir -p /usr/local/lib /usr/local/bin \
			&& wget -nv -O /tmp/code-server.tar.gz https://github.com/coder/code-server/releases/download/v${CODE_VERSION}/code-server-${CODE_VERSION}-linux-amd64.tar.gz \
			&& tar -C /usr/local/lib -xzf /tmp/code-server.tar.gz \
			&& mv -f /usr/local/lib/code-server-${CODE_VERSION}-linux-amd64 /usr/local/lib/code-server-${CODE_VERSION} \
			&& ln -fs /usr/local/lib/code-server-${CODE_VERSION}/bin/code-server /usr/local/bin/code-server \
			&& rm -f /tmp/code-server.tar.gz

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
