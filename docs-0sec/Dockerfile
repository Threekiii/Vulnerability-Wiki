From node:10-alpine
RUN npm install cnpm -g --registry=https://registry.npm.taobao.org
RUN cnpm i docsify-cli -g

WORKDIR /data
COPY docs /data/docs

CMD ["/usr/local/bin/docsify","serve","docs","--port","3002"]
