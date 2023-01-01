FROM node:16-alpine as builder
USER node
WORKDIR '/home/node/app'
RUN mkdir -p "/home/node/app"
COPY --chown=node:node  ./package.json ./
RUN npm install
COPY --chown=node:node . .
CMD ["npm", "run", "build"]

FROM ngnix
EXPOSE 80
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /home/node/app/build /usr/share/ngnix/html