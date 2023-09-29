FROM nginxinc/nginx-unprivileged:1.19-alpine
LABEL maintainer="gielee.com"

COPY ./default.conf.tpl /etc/nginx/default.conf.tpl
COPY ./uwsgi_params /etc/nginx/uwsgi_params
COPY ./run.sh /run.sh

ENV LISTEN_PORT=8000
ENV APP_HOST=app
ENV APP_PORT=9000

USER root

RUN mkdir -p /vol/static && \
    chmod -R 755 /vol && \
    touch /etc/nginx/conf.d/default.conf && \
    chown -R nginx:nginx /etc/nginx/conf.d/default.conf && \
    chmod -R +x /run.sh

VOLUME /vol/static

USER nginx

CMD ["/run.sh"]
