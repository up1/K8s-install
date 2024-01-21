FROM node:21-alpine3.18 as step01
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.25.3-alpine
COPY nginx_reverse.conf /etc/nginx/conf.d/default.conf
COPY --from=step01 /app/dist/demo-angular/browser /usr/share/nginx/html
EXPOSE 80