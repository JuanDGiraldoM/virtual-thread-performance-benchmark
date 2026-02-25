##
## Build
##
FROM golang:1.26.0-alpine3.23 AS build
WORKDIR /app

COPY go.mod .
COPY go.sum .
RUN go mod download
 
COPY . .
RUN go build -o /go-ms

 
##
## Deploy
##
FROM alpine:3.23
WORKDIR /

COPY --from=build /go-ms /go-ms
CMD ["/go-ms"]