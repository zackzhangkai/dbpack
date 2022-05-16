FROM golang:1.16.3 as builder
WORKDIR /app
ADD . /app
RUN make build-local

FROM alpine:latest
WORKDIR /
COPY --from=builder /app/dbpack /dbpack
COPY --from=builder /app/docker/scripts/wait-for-mysql.sh /wait-for-mysql.sh
CMD ["/dbpack", "start", "-c", "config.yaml"]
