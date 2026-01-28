FROM golang:1.23-alpine AS builder
WORKDIR /app
COPY main.go .
RUN go build -o hello main.go

FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/hello .
ENTRYPOINT ["./hello"]  