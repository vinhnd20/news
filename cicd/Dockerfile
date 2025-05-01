FROM klakegg/hugo:latest AS builder
WORKDIR /site
COPY . .
RUN hugo --minify

FROM klakegg/hugo:latest
WORKDIR /site
COPY --from=builder /site/public /site/public
EXPOSE 80
CMD ["hugo", "server", "--bind", "0.0.0.0", "--port", "80", "--baseURL", "/", "--appendPort=false"]