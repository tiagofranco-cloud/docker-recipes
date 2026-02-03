FROM ubuntu:22.04

LABEL maintainer="tiagofranco.cloud@gmail.com"

ENV APP_VERSION="1.0.0"

RUN apt-get update \
  && apt-get install -y --no-install-recommends nginx \
  && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html

COPY ./html/index.html /var/www/html/index.html

EXPOSE 80
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]