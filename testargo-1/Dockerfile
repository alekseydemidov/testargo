FROM golang:1.19
WORKDIR /usr/local/go/src/app
COPY main.go ./
ENV CGO_ENABLED=0
RUN go mod init main && go build  main .

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=0 /usr/local/go/src/app/main ./
CMD ["/root/main"]

