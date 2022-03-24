FROM node:16 AS builder

WORKDIR /usr/app

COPY package*.json ./

RUN yarn

COPY . .

RUN yarn build

FROM nginx
EXPOSE 80
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/app/dist /usr/share/nginx/html

CMD ["yarn", "preview"]