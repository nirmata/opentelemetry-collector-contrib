FROM alpine:latest as prep
RUN apk --update add ca-certificates

RUN mkdir -p /tmp
USER 65532:65532

FROM scratch

COPY --from=prep /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
COPY otelcontribcol /
EXPOSE 4317 55680 55679
USER 65532:65532
ENTRYPOINT ["/otelcontribcol"]
CMD ["--config", "/etc/otel/config.yaml"]
