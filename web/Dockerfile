# Stage 1: Build binary
FROM golang:1.22 AS builder
WORKDIR /app
COPY dispatcher.go .

RUN CGO_ENABLED=0 GOOS=linux go build -o dispatcher dispatcher.go

# Stage 2: Alpine runtime
FROM alpine:latest
WORKDIR /app
COPY ./static ./static
COPY --from=builder /app/dispatcher /app/dispatcher

EXPOSE 80
ENTRYPOINT ["/app/dispatcher"]