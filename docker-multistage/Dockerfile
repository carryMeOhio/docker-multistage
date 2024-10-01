# Stage 1: Build the application
FROM golang:1.20 AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN go build -o docker-multistage

# Stage 2: Create the final lightweight image
FROM alpine:latest

WORKDIR /root/
COPY --from=builder /app/docker-multistage .

CMD ["./docker-multistage"]