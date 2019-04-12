FROM golang:1.8

RUN printf "deb http://archive.debian.org/debian/ jessie main\ndeb-src http://archive.debian.org/debian/ jessie main\ndeb http://security.debian.org jessie/updates main\ndeb-src http://security.debian.org jessie/updates main" > /etc/apt/sources.list
RUN apt-get update && apt-get install -y libpcap0.8-dev

WORKDIR /go/src/app
COPY . .

RUN go-wrapper download
RUN go-wrapper install

ARG DEV=lo
ENV DEV=lo

CMD ["sh", "-c", "go-wrapper run -devName=$DEV -clickhouseAddress localhost:9000"]
