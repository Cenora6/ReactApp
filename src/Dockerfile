FROM node:18.4.0 AS build

LABEL version="1.0"

WORKDIR /src
COPY ailurus .
RUN npm install --production

RUN npm run build

FROM nginx:alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=build /src/build .
ENTRYPOINT ["nginx", "-g", "daemon off;"]