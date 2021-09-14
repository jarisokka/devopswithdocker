FROM golang:alpine AS build

EXPOSE 8080

WORKDIR /app

COPY . .

ENV REQUEST_ORIGIN=http://localhost:5000

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" 



FROM scratch

WORKDIR /app

COPY --from=build /app/server /usr/bin/

ENTRYPOINT ["server"]

