ARG USER_UID=65532:65532

FROM alpine:latest as prep
ARG USER_UID
RUN apk --update add ca-certificates

RUN mkdir -p /tmp
USER ${USER_UID}

FROM scratch
ARG USER_UID

COPY --from=prep /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
COPY otelcontribcol /
EXPOSE 4317 55680 55679
USER ${USER_UID}
ENTRYPOINT ["/otelcontribcol"]
CMD ["--config", "/etc/otel/config.yaml"]
