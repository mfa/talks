FROM debian:stable

WORKDIR /opt/code

RUN apt-get update && apt-get install -y curl gnupg
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
RUN apt-get install -y nodejs

RUN npm install -g reveal-md

COPY . /opt/code
WORKDIR /opt/code

EXPOSE 1948

CMD ["sh", "-c", "reveal-md /opt/code/ -w"]
