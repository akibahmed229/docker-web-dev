FROM node:20-alpine3.18

# RUN addgroup app && adduser -S -G app app

# USER app

WORKDIR /app

COPY package*.json ./

RUN yarn install

COPY . .

EXPOSE 5173

CMD yarn run dev
