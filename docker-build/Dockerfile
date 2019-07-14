FROM alpine:3.10

RUN apk --no-cache add git docker-cli

COPY ./scripts/build /bin/docker-build
RUN chmod 755 /bin/docker-build

ENTRYPOINT /bin/docker-build
