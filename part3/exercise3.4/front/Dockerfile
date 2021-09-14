FROM ubuntu:18.04

EXPOSE 5000

WORKDIR /usr/src/app

COPY package*.json ./

RUN apt-get update && apt-get install -y curl && \
    curl -sL https://deb.nodesource.com/setup_lts.x | bash - && \
    apt install -y nodejs && \
    apt-get purge -y --auto-remove curl && \ 
    rm -rf /var/lib/apt/lists/* && \
    useradd -m appuser

COPY . .

RUN npm install

ENV REACT_APP_BACKEND_URL=http://localhost:8080

RUN npm run build

RUN npm install -g serve

USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]