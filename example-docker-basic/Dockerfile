FROM node AS NodeBuilder

WORKDIR /app

COPY ./package.json .
COPY ./package-lock.json .

RUN npm i

COPY ./public .
COPY ./src .

RUN npm run build

FROM nginx
WORKDIR /nginx
COPY --from=NodeBuilder ./app/build ./usr/share/nginx/html

EXPOSE 80
