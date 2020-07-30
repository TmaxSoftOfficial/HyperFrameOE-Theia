FROM centos:7
# version 20.0

# 0) install required packages using yum
RUN yum update -y && yum install -y \
  make \
  gcc \
  gcc-c++ \
  wget \
  build-essential \
  gettext-base \
  git \
  jq \
  curl \
  java-1.8.0-openjdk-devel

# 1) copy NodeSource Node.js
COPY ./nodesource.bat /tmp/
COPY ./cf-cli_6.47.2_linux_x86-64.tgz /tmp/

# 2) set NodeSource Node.js and install
RUN cat /tmp/nodesource.bat | bash -
RUN yum install -y nodejs

# 3) install yarn (package manager)
RUN npm install -g yarn

# 4) set command line client for Cloud Foundry
RUN cd /usr/local/bin && \
  mv /tmp/cf-cli_6.47.2_linux_x86-64.tgz /usr/local/bin && \
  tar zxvf cf-cli_6.47.2_linux_x86-64.tgz

# 5) make theia app directory
RUN mkdir /theia-app
ADD package.json /theia-app
WORKDIR /theia-app
# using "NODE_OPTIONS=..." to avoid out-of-memory problem in CI

# 6) set theia plugin path
ENV SHELL=/bin/bash \
    THEIA_DEFAULT_PLUGINS=local-dir:/theia-app/plugins

# 7) theia build
RUN yarn --cache-folder ./ycache && rm -rf ./ycache && \
    NODE_OPTIONS="--max_old_space_size=8192" yarn theia build ; \
    yarn theia download:plugins

# 8) add extra plugin
ADD plugins/*.vsix /theia-app/plugins/

ENTRYPOINT [ "yarn",  "theia", "start", "--hostname=0.0.0.0", "/home/project" ]
EXPOSE 3000

