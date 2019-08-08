# usage
#  docker container run -d -p 80 -p 8080 -v \\.\pipe\docker_engine:\\.\pipe\docker_engine sixeyed/traefik:v1.7.12-windowsnanoserver-1809 --api --docker --docker.endpoint=npipe:////./pipe/docker_engine --logLevel=DEBUG
FROM mcr.microsoft.com/windows/nanoserver:1809

COPY --from=traefik:v1.7.12-nanoserver /traefik.exe /traefik.exe
# uses netapi32.dll which is not included in Nano Server 1809, copy from servercore 1809
COPY --from=mcr.microsoft.com/windows/servercore:1809 /windows/system32/netapi32.dll /windows/system32/netapi32.dll

EXPOSE 80
ENTRYPOINT ["/traefik"]

# Metadata (copied from official Traefik image)
LABEL org.label-schema.vendor="Containous" \
      org.label-schema.url="https://traefik.io" \
      org.label-schema.name="Traefik" \
      org.label-schema.description="A modern reverse-proxy" \
      org.label-schema.version="v1.7.12" \
      org.opencontainers.image.documentation="https://docs.traefik.io"
