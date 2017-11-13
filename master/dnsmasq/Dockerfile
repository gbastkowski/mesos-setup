FROM alpine:edge
RUN apk --no-cache add dnsmasq
EXPOSE 53 53/udp
COPY dnsmasq.conf /usr/local/etc/
ENTRYPOINT ["dnsmasq", "-k"]
