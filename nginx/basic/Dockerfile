FROM ubuntu:22.04 AS builder
WORKDIR /site
COPY ./html/index.html ./index.html

FROM alpine:3.20
RUN apk add --no-cache nginx curl

WORKDIR /var/www/html
COPY --from=builder /site/index.html /var/www/html/index.html
COPY ./conf/default.conf /etc/nginx/http.d/default.conf

EXPOSE 80
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]

HEALTHCHECK --interval=30s --timeout=3s --retries=3 \
  CMD curl -f http://localhost/ || exit 1
