FROM node:18 AS build

WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build ../public

FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html
COPY ../src/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
