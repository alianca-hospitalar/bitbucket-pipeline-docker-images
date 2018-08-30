FROM amazonlinux:latest

# Enable user creation and helper packages
RUN yum install -y shadow-utils tar gzip
RUN adduser -ms /bin/bash nodejs

# Installing AWS CLI and AWS EB CLI
RUN curl -O -s https://bootstrap.pypa.io/get-pip.py \
  && python get-pip.py \
  && pip install awscli \
  && pip install awsebcli

# Install node with nodejs user
USER nodejs
WORKDIR /home/nodejs

# Installing Node.js
RUN curl -O -s https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh \
  && sh install.sh

ENV NVM_DIR /home/nodejs/.nvm
ARG NODE_VERSION

RUN source $NVM_DIR/nvm.sh \
  && nvm install $NODE_VERSION \
  && nvm alias default $NODE_VERSION \
  && nvm use default

# Persisting environment variables changed by nvm
ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

# Confirm Node.js installation
RUN node -v && npm -v

# Installing yarn
RUN npm install --global yarn

# Confirm yarn installation
RUN yarn --version
