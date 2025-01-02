FROM debian:bullseye-slim

RUN apt update && apt upgrade -y && apt install -y nano curl wget iputils-ping net-tools iproute2 dnsutils

CMD ["tail", "-f", "/dev/null"]
