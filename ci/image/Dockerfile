FROM centos:7

RUN yum update -y && yum install -y \
  devtoolset-6 \
  gcc-c++ \
  xz \
  ccache \
  git \
  wget \
  openssl \
  libxkbfile-devel \
  libsecret-devel \
  libx11-devel

RUN mkdir /usr/share/node && cd /usr/share/node \
  && curl "https://nodejs.org/dist/v12.14.0/node-v12.14.0-linux-$(uname -m | sed 's/86_//; s/aarch/arm/').tar.xz" | tar xJ --strip-components=1 --
ENV PATH "$PATH:/usr/share/node/bin"
RUN npm install -g yarn@1.22.4

RUN curl -L "https://github.com/mvdan/sh/releases/download/v3.0.1/shfmt_v3.0.1_linux_$(uname -m | sed 's/x86_/amd/; s/aarch64/arm/')" > /usr/local/bin/shfmt \
  && chmod +x /usr/local/bin/shfmt

ENTRYPOINT ["/bin/bash", "-c"]
