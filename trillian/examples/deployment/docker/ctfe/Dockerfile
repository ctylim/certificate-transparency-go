FROM golang:1.11 as build

ADD . /go/src/github.com/ctylim/certificate-transparency-go-p192
WORKDIR /go/src/github.com/ctylim/certificate-transparency-go-p192

ARG GOFLAGS=""
ENV GOFLAGS=$GOFLAGS
ENV GO111MODULE=on
RUN go get ./trillian/ctfe/ct_server

FROM gcr.io/distroless/base

COPY --from=build /go/bin/ct_server /

ENTRYPOINT ["/ct_server"]
