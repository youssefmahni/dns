FROM debian:bullseye-slim

# Install Required Packages
RUN apt update && apt upgrade -y && apt install -y nano curl wget iputils-ping net-tools iproute2 dnsutils

# Install Bind9
RUN apt install bind9 bind9utils -y

# Configure DNS Server Options
COPY named.conf.options /etc/bind/named.conf.options

# Create DNS Zone and Zone Files
COPY named.conf.local /etc/bind/named.conf.local
RUN mkdir /etc/bind/zones
RUN chown root:bind /etc/bind/zones
COPY forward.ysf.con.db /etc/bind/zones/forward.ysf.con.db
COPY reverse.192.1.1.db /etc/bind/zones/reverse.192.1.1.db

# disable ipv6
RUN echo 'OPTIONS="-u bind -4"' > /etc/default/named

EXPOSE 53

CMD ["named", "-g"]