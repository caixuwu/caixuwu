FROM python:3.7.0-alpine3.8
LABEL mantainer="caixuwu <caixuwu@outlook.cn>"

ADD requirements /usr/local/

RUN apt-get update \
    && apt-get install -y --no-install-recommends make g++ git \
    && cd /root/
    && git clone --recursive https://github.com/dmlc/xgboost
    && pip --no-cache-dir install -r /usr/local/requirements \
    && apt-get purge -y --auto-remove git make libssl-dev \


