#stage 1
FROM node:17-alpine as builder
WORKDIR .
COPY package.json
COPY package-lock.json
RUN npm install
COPY . .
RUN npm run server

#stage 2
FROM nginx:1.19.0
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=builder ./build .
ENTRYPOINT ["nginx","-g","daemon off;"]
