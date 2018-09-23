FROM python:3-alpine

ENV RUNTIME_PACKAGES openssl-dev libxslt-dev
ENV BUILD_PACKAGES build-base libxml2-dev libffi-dev

# looks like scrapyd-deploy can't handle dependancies us and dateparser manually adding until this is fixed
# https://stackoverflow.com/questions/46389882/scrapy-deploy-to-scrapyd-doesnt-install-requirements-pointed-in-setup-py
ENV MY_PACKAGES us dateparser

RUN apk update && \
        apk add --no-cache $BUILD_PACKAGES $RUNTIME_PACKAGES && \
        mkdir -p /scrapyd/data && \
        pip --no-cache-dir install scrapyd $MY_PACKAGES && \
        apk del $BUILD_PACKAGES

WORKDIR /scrapyd

ENV TZ=UTC

COPY scrapyd.conf /etc/scrapyd/scrapyd.conf

EXPOSE 6800
CMD ["scrapyd", "--pidfile="]
