FROM python:3-alpine

ENV BUILD_PACKAGES build-base

RUN apk update && \
        apk add --no-cache $BUILD_PACKAGES && \
        mkdir /spiderkeeper && \
        pip install spiderkeeper && \
        apk del $BUILD_PACKAGES

WORKDIR /spiderkeeper

ENV TZ=UTC
ENV SCRAPY_SERVER=http://scrapyd:6800
ENV SPIDERKEEPER_USERNAME=admin
ENV SPIDERKEEPER_PASSWORD=admin

EXPOSE 5000
CMD ["sh", "-c", "spiderkeeper --server=$SCRAPY_SERVER --username=$SPIDERKEEPER_USERNAME --password=$SPIDERKEEPER_PASSWORD"]
