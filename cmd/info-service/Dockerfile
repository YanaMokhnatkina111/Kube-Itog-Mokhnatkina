FROM golang:1.24.9-alpine3.22 AS builder

WORKDIR /app

COPY ./cmd/info-service .
COPY go.mod .

RUN go mod tidy

RUN go build -o info-service /app/main.go

FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/info-service .

CMD [ "/app/info-service"]

EXPOSE 8080