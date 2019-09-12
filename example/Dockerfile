FROM python:3.6-alpine
WORKDIR /usr/src/app

RUN apk add --no-cache --virtual \
        .build-deps \
        gcc \
        g++ \
        musl-dev \
        python3-dev \
        supervisor \
        redis

COPY ./requirements.txt /usr/src/app

RUN pip install -r requirements.txt

COPY . /usr/src/app

EXPOSE  6379:6379

ENV C_FORCE_ROOT=1

CMD ["/usr/bin/supervisord", "-c", "/usr/src/app/supervisord.conf"]
