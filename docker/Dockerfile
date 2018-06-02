FROM nginx:1.14

MAINTAINER Qianzhou Xu <xuqianzhou@gmail.com>

ENV NVM_VERSION=0.33.2 \
    HOME=/root

ADD default.conf /etc/nginx/conf.d/default.conf

WORKDIR /usr/share/nginx/html

RUN apt-get update && apt-get install -y \
    curl \
    git-core \
  && rm -rf /var/lib/apt/lists/* \
  && curl -o- https://raw.githubusercontent.com/creationix/nvm/v${NVM_VERSION}/install.sh | bash \
  && . $HOME/.nvm/nvm.sh \
  && nvm install stable \
  && npm install -g hexo-cli \
  && mkdir -p $HOME/temp \
  && hexo init $HOME/temp \
  && mv $HOME/temp/* /usr/share/nginx/html \
  && hexo generate

CMD nginx -g "daemon off;"
