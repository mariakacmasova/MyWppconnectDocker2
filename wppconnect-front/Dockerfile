FROM node:14.17-alpine3.13 as builder

RUN apk add wget && \
    apk add --no-cache git

WORKDIR /home/node
RUN git clone https://github.com/markinhok2/wppconnect-frontend.git /home/node/app

WORKDIR /home/node/app
COPY ./config.js /home/node/app/public
RUN yarn install

FROM node:14.17-alpine3.13
WORKDIR /home/node/app
RUN apk add chromium
COPY --from=builder /home/node/app .
EXPOSE 3000