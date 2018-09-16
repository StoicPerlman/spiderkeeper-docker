FROM python:3-alpine

RUN apk update && apk add build-base libxml2-dev libxslt-dev libffi-dev openssl-dev

RUN mkdir /scrapyd
WORKDIR /scrapyd

RUN pip install scrapyd

# looks like scrapyd-deploy can't handle dependancies manually adding until this is fixed
# https://stackoverflow.com/questions/46389882/scrapy-deploy-to-scrapyd-doesnt-install-requirements-pointed-in-setup-py
RUN pip install us dateparser

RUN apk del build-base

ENV TZ=UTC

COPY scrapyd.conf /etc/scrapyd/scrapyd.conf

EXPOSE 6800
CMD ["scrapyd"]
