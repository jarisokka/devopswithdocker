FROM node:alpine AS build

EXPOSE 5000

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

ENV REACT_APP_BACKEND_URL=http://localhost:8080

RUN npm run build



FROM node:alpine

COPY --from=build /usr/src/app/build /build

RUN adduser -D appuser

RUN npm install -g serve

USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]