FROM golang:1.24.9-alpine3.22 AS builder

WORKDIR /app

COPY ./cmd/api-service .
COPY go.mod .

RUN go mod tidy

RUN go build -o api-service /app/main.go

FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/api-service .

EXPOSE 8080

CMD [ "/app/api-service"]

ENTRYPOINT ["./server"]