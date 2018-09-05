FROM alpine:3.8

# Based upon https://hub.docker.com/r/hermsi/alpine-sshd/~/dockerfile/
LABEL Maintainer "Andreas Elser"
LABEL Version "0.1"

ENV ROOT_PASSWORD root

RUN apk add --no-cache openssh \
        && sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config \
        && echo "root:${ROOT_PASSWORD}" | chpasswd \
        && rm -rf /var/cache/apk/* /tmp/*

ADD ./entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint.sh

EXPOSE 22

ENTRYPOINT [ "entrypoint.sh" ]