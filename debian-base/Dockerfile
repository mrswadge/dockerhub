FROM debian:stretch
MAINTAINER Stuart Stephen <stuart.stephen@gmail.com>

ENV TINI_VERSION 0.18.0
ENV TINI_URL https://github.com/krallin/tini/releases/download/v$TINI_VERSION/tini
ENV TINI_KILL_PROCESS_GROUP 1

ADD ["cleanimage", "/usr/local/bin/"]
ADD ["my_init", "/usr/local/bin/"]
ADD ["appfolders", "/usr/local/bin/"]

RUN chmod +x "/usr/local/bin/cleanimage" 
RUN chmod +x "/usr/local/bin/my_init" 
RUN chmod +x "/usr/local/bin/appfolders" 

RUN apt-get update \
 && apt-get dist-upgrade -y \
 && apt-get install -y \
      apt-transport-https \
      ca-certificates \
      curl \
      nano \
      unzip \
 && cleanimage

RUN curl -Lo "/usr/local/bin/tini" $TINI_URL \
 && chmod +x "/usr/local/bin/tini"

RUN mkdir "/etc/my_init.d"

RUN echo "appfolders link &> /var/log/appfolders.log" > "/etc/my_init.d/000-link-appfolders" \
 && chmod +x "/etc/my_init.d/000-link-appfolders"

RUN "/usr/local/bin/cleanimage"

ENTRYPOINT ["tini", "--", "my_init"]