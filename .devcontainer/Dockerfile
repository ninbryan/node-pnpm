FROM ubuntu:18.04

WORKDIR /home/

COPY . .

# https://github.com/nvm-sh/nvm#additional-notes
ENV NODE_VERSION 12.16.3

RUN bash ./setup.sh

RUN echo 'export NVM_DIR="$HOME/.nvm"' >> "$HOME/.zshrc"
RUN echo '\n' >> "$HOME/.zshrc"
RUN echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm' >> "$HOME/.zshrc"

# install node and npm
RUN source $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && nvm use default

# install pnpm
# https://pnpm.js.org/
RUN npx pnpm add -g pnpm

# check installations
RUN node -v
RUN npm -v
RUN npx -v
RUN pnpm -v

