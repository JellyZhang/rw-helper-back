FROM golang:1.15-alpine3.12 as builder

RUN mkdir /app

WORKDIR /app

COPY ./internal/ .

RUN GO111MODULE=on go build -o main .

#
FROM alpine:3.12

WORKDIR /root/

COPY --from=builder /app/main .
COPY --from=builder /app/config.toml .

EXPOSE 8080

CMD ["./main"]
