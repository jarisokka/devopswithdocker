FROM ubuntu:18.04 AS build

EXPOSE 8080

WORKDIR /usr/src/app

RUN apt-get update && apt-get install -y curl && \
    curl -sL https://golang.org/dl/go1.17.1.linux-amd64.tar.gz | tar -xz -C /usr/local && \
    apt-get purge -y --auto-remove curl && \ 
    rm -rf /var/lib/apt/lists/* && \
    useradd -m appuser

COPY . .

ENV REQUEST_ORIGIN=http://localhost:5000

RUN /usr/local/go/bin/go build

USER appuser


FROM ubuntu:18.04

WORKDIR /usr/src/app

COPY --from=build /usr/src/app /usr/src/app

RUN useradd -m appuser

USER appuser

CMD ["./server"]
