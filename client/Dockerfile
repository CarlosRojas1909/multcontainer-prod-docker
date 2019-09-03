FROM node:alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
# this line is setting nginx to use default.conf file configuration
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# we are copying everything from running npm run build from previous step into a file in nginx to render our build file(htm. js)
COPY --from=builder /app/build /usr/share/nginx/html