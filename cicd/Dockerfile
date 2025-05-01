FROM klakegg/hugo:latest AS builder
WORKDIR /site
COPY . .
RUN hugo --minify

FROM nginx:alpine
COPY --from=builder /site/public /usr/share/nginx/html
COPY cicd/nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]