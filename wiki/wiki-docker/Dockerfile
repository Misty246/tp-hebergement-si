FROM node:18-alpine
RUN apk add --no-cache wget tar
RUN wget https://github.com/Requarks/wiki-v2/releases/latest/download/wiki-js.tar.gz
RUN mkdir /wiki && \
    tar xzf wiki-js.tar.gz -C /wiki && \
    rm wiki-js.tar.gz

WORKDIR /wiki
RUN mv config.sample.yml config.yml
EXPOSE 3000
CMD ["node", "server"]
