FROM golang:1.19.3 as BUILDER

WORKDIR /go/src/app
COPY hello-word.go .

RUN apt update && apt install -y upx

RUN go build -ldflags "-s -w" hello-word.go
RUN chmod +x hello-word
RUN upx --force hello-word

ENTRYPOINT ["/go/src/app/hello-word"]


FROM hello-world
WORKDIR /app
COPY --from=BUILDER /go/src/app/hello-word .
ENTRYPOINT ["/app/hello-word"]
