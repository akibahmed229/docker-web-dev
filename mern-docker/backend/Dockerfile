FROM node:20-alpine

#RUN addgroup app && adduser -S -G app app
#USER app

WORKDIR /app

COPY package*.json ./

#USER root
#RUN chown -R app:app .
#USER app

RUN yarn install

COPY . .

EXPOSE 8000

CMD yarn start
