FROM python:3.11.0-slim-bullseye

ENV APP_PATH="/usr/src/app" \
    APP_USER="admin" \
    PYTHONUNBUFFERED=1 \
    DJANGO_SETTINGS_MODULE="server.settings"

WORKDIR ${APP_PATH}
RUN adduser $APP_USER

COPY . .
RUN mv entrypoint.sh /
RUN cat /etc/hosts
RUN chown -R $APP_USER $APP_PATH
RUN chown -R $APP_USER /entrypoint.sh
RUN chmod +x /entrypoint.sh

RUN apt-get update
RUN apt-get -y install gcc libjpeg62-turbo-dev zlib1g-dev nano

RUN python3 -m pip install --upgrade pip
RUN python3 -m pip install -r requirements.txt --no-cache-dir

EXPOSE 8080
USER $APP_USER
ENTRYPOINT ["/entrypoint.sh"]
