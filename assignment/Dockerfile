FROM ubuntu:24.04 AS build

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends curl ca-certificates

RUN curl -LO https://go.dev/dl/go1.23.6.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go1.23.6.linux-amd64.tar.gz && \
    rm go1.23.6.linux-amd64.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"

COPY main.go .

RUN CGO_ENABLED=0 go build -o hello main.go

FROM alpine:latest

WORKDIR /app

COPY --from=build /app/hello .

ENTRYPOINT ["./hello"]
