FROM python:3-alpine

RUN apk update && apk add build-base

RUN mkdir /spiderkeeper
WORKDIR /spiderkeeper

RUN pip install spiderkeeper

RUN apk del build-base

ENV TZ=UTC
ENV SCRAPY_SERVER=http://scrapyd:6800
ENV SPIDERKEEPER_USERNAME=admin
ENV SPIDERKEEPER_PASSWORD=admin

EXPOSE 5000
CMD ["sh", "-c", "spiderkeeper --server=$SCRAPY_SERVER --username=$SPIDERKEEPER_USERNAME --password=$SPIDERKEEPER_PASSWORD"]
