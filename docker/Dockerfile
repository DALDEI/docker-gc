FROM gliderlabs/alpine:3.2
# https://docs.docker.com/engine.reference/builder/#/shell
# allow supplying version and also default it
ARG DOCKER_VERSION
ENV DOCKER_VERSION ${DOCKER_VERSION:-1.6.2}

# We get curl so that we can avoid a separate ADD to fetch the Docker binary, and then we'll remove it
RUN apk --update add bash curl \
  && cd /tmp/ \
  && curl -sSL -O https://get.docker.com/builds/Linux/x86_64/docker-${DOCKER_VERSION}.tgz \
  && tar zxf docker-${DOCKER_VERSION}.tgz \
  && mkdir -p /usr/local/bin/ \
  && mv $(find . -name 'docker' -type f) /usr/local/bin/ \
  && chmod +x /usr/local/bin/docker \
  && apk del curl \
  && rm -rf /tmp/* \
  && rm -rf /var/cache/apk/*

COPY ./docker-gc /docker-gc

VOLUME /var/lib/docker-gc

CMD ["/docker-gc"]
