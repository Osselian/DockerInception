FROM alpine:latest

# Установка nginx и OpenSSL
RUN apk update && apk add --no-cache nginx openssl

# Создание необходимых директорий
RUN mkdir -p /run/nginx && mkdir -p /etc/nginx/ssl

# Копирование пользовательского конфигурационного файла nginx
# Файл nginx.conf должен содержать строку:
#    ssl_protocols TLSv1.2 TLSv1.3;
# в нужном серверном блоке
COPY nginx.conf /etc/nginx/nginx.conf

# Копирование SSL-сертификата и ключа (если они есть)
COPY cert.crt /etc/nginx/ssl/cert.crt
COPY cert.key /etc/nginx/ssl/cert.key

# Экспонирование порта для HTTPS
EXPOSE 443

# Запуск nginx в foreground
CMD ["nginx", "-g", "daemon off;"]