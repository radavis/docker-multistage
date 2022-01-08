# syntax=docker/dockerfile:1
FROM golang:1.16 AS builder
ENV GO111MODULE=auto
WORKDIR /go/src/github.com/alexellis/href-counter/
RUN go get -d -v golang.org/x/net/html
COPY app.go ./

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
# COPY --from=<stage_index> ...
COPY --from=builder /go/src/github.com/alexellis/href-counter/app ./
CMD ["./app"]
