FROM debian:jessie

MAINTAINER Tam Vu <vmintam@gmail.com>

# Set environment.
#ENV \
#  DEBIAN_FRONTEND=noninteractive \
#    TERM=xterm-color

    # Install packages.
RUN apt-get update && apt-get -y install \
      build-essential \
      curl \
      libreadline-dev \
      libncurses5-dev \
      libpcre3-dev \
      libssl-dev \
      nano \
      perl \
      wget

     # Compile openresty from source.
RUN \
      wget https://openresty.org/download/openresty-1.9.7.4.tar.gz && \
      tar -xzvf openresty-*.tar.gz && \
      rm -f openresty-*.tar.gz && \
      cd openresty-* && \
      ./configure --with-pcre-jit --with-ipv6 && \
      make && \
      make install && \
      make clean && \
      cd .. && \
      rm -rf openresty-*&& \
      ln -s /usr/local/openresty/nginx/sbin/nginx /usr/local/bin/nginx && \
      ldconfig && \
      useradd -s /sbin/nologin nginx && \
      touch /var/run/nginx.pid && \
      mkdir -p /var/log/nginx && \
      chown -R nginx.nginx /var/run/nginx.pid && \
      chown -R nginx.nginx /var/log/nginx


# Set the working directory.
WORKDIR /home/openresty

# Add files to the container.
ADD ./entrypoint /home/openresty

RUN mkdir -p /video/nginx/cache && chown -R nginx.nginx /video/nginx/cache
# Expose volumes.
VOLUME ["/etc/nginx"]

# Set the entrypoint script.
#ENTRYPOINT ["./entrypoint"]

# Define the default command.
CMD ["nginx", "-c", "/etc/nginx/nginx.conf"]
