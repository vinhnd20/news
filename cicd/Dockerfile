FROM alpine:3.18 AS build

# Cài Hugo phiên bản cụ thể, không cache
RUN apk add --update hugo

WORKDIR /opt/HugoApp

# Copy mã nguồn Hugo
COPY . .

# Build website với minify
RUN hugo --minify

# Stage 2: Serve với Nginx
FROM nginx:1.25-alpine

# Copy file cấu hình Nginx tùy chỉnh
COPY cicd/nginx/nginx.conf /etc/nginx/conf.d/default.conf

# Copy file tĩnh từ stage build
COPY --from=build /opt/HugoApp/public /usr/share/nginx/html

# Đặt quyền cho Nginx
RUN chown -R nginx:nginx /usr/share/nginx/html

# Expose port 80 và 443
EXPOSE 80/tcp 443/tcp
