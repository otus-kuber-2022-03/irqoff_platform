FROM nginx:1.21.6

LABEL maintainer="Alexander Usov <irqoff@gmail.com>"

ENV USER   otus
ENV GROUP  otus
ENV UID    1001
ENV GID    1001

RUN set -x \
# create nginx user/group
    && addgroup --gid $GID "$GROUP" \
    && adduser --disabled-login --ingroup "$GROUP" --no-create-home --home /nonexistent --gecos "otus user" --shell /bin/false --uid "$UID" "$USER" \
    && sed -i '/listen/s@80@8000@; /root/s@/usr/share/nginx/html@/app@' /etc/nginx/conf.d/default.conf \
    && sed -i '/^user/d' /etc/nginx/nginx.conf \
    && chown -R "$USER":root /var/cache/nginx \
    && touch /run/nginx.pid \
    && chown -R "$USER":root /run/nginx.pid

USER "$USER"
EXPOSE 8000
