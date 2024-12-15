# Use the official Go image as base
FROM golang:1.19-alpine as build

WORKDIR /app

COPY . .

RUN go build -o go-service .

# Second stage: Create the minimal production image
FROM alpine:latest

WORKDIR /app

COPY --from=build /app/go-service .

EXPOSE 8081

CMD ["./go-service"]