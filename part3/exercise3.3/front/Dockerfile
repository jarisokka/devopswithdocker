FROM ruby:3.0.0

EXPOSE 5000

WORKDIR /usr/src/app

RUN curl -sL https://deb.nodesource.com/setup_lts.x | bash -
RUN apt install -y nodejs

COPY . .

RUN npm install

ENV REACT_APP_BACKEND_URL=http://localhost:8080

RUN npm run build

RUN npm install -g serve

RUN useradd -m appuser

USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]