FROM alpine:latest

RUN apk update && apk add --no-cache nginx openssl

RUN mkdir -p /run/nginx && mkdir -p /etc/nginx/ssl

RUN openssl req -x509 -nodes -days 30 \
	-subj "/C=AM/L=YVN/O=42/CN=sosokin.42.fr" \
	-newkey rsa:2048 -keyout /etc/nginx/ssl/sosokin.42.fr.key -out /etc/nginx/ssl/sosokin.42.fr.crt

# COPY nginx.conf /etc/nginx/nginx.conf

# Экспонирование порта для HTTPS
EXPOSE 443

# Запуск nginx в foreground
CMD ["nginx", "-g", "daemon off;"]
