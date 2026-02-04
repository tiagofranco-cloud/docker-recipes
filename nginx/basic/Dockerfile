FROM ubuntu:22.04

LABEL maintainer="tiagofranco.cloud@gmail.com"

ENV APP_VERSION="1.0.0"

RUN apt-get update \
  && apt-get install -y --no-install-recommends nginx curl \
  && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html

COPY ./html/index.html /var/www/html/index.html

EXPOSE 80
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]

HEALTHCHECK --interval=30s --timeout=3s --retries=3 \
  CMD curl -f http://localhost/ || exit 1