FROM node:14-alpine as build
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY .env* ./
COPY src/ ./src/
COPY public/ ./public/
RUN npm run build

FROM nginx:latest
COPY --from=build /public /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]