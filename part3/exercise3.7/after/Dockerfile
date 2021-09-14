FROM node:alpine AS build

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build


FROM node:alpine

COPY --from=build /usr/src/app/build /build

RUN adduser -D appuser

RUN npm install -g serve

USER appuser

CMD ["serve", "-s", "build"]

#after build run with docker run -d -p 5000:5000 <imagename>
