# Stage 1: Build Hugo site
FROM klakegg/hugo:0.111.3 AS builder
WORKDIR /site
COPY . .
RUN hugo --minify

# Stage 2: Serve site with Hugo server
FROM klakegg/hugo:0.111.3
WORKDIR /site
COPY --from=builder /site/public /site/public
EXPOSE 80
# Chạy Hugo server với cấu hình rõ ràng
CMD ["hugo", "server", "--bind=0.0.0.0", "--port=80", "--baseURL=/", "--appendPort=false", "--source=/site/public"]