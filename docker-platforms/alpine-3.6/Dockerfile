FROM alpine:3.6

MAINTAINER James Cuzella @trinitronx https://keybase.io/trinitronx/

RUN set -x                  && \
    apk --update upgrade    && \
    apk add ca-certificates && \
    apk add build-base      && \
    apk add git bash        && \
    apk add autoconf        && \
    apk add automake        && \
    apk add libtool gettext && \
    rm -rf /var/cache/apk/*

## Enable running /sbin/init as pid 1 for this container
## This can help to run traditional build scripts which expect
## to be running on a full Linux system with init
## Source: https://github.com/neeravkumar/dockerfiles/blob/master/alpine-openrc/Dockerfile

# use the CDN mirror from gilderlabs since its much faster
RUN mkdir -p /etc/apk && echo "http://alpine.gliderlabs.com/alpine/edge/main" > /etc/apk/repositories &&\
# Install openrc
    apk update && apk add openrc &&\
# Tell openrc its running inside a container, till now that has meant LXC
    sed -i 's/#rc_sys=""/rc_sys="lxc"/g' /etc/rc.conf &&\
# Tell openrc loopback and net are already there, since docker handles the networking
    echo 'rc_provide="loopback net"' >> /etc/rc.conf &&\
# no need for loggers
    sed -i 's/^#\(rc_logger="YES"\)$/\1/' /etc/rc.conf &&\
# can't get ttys unless you run the container in privileged mode
    sed -i '/tty/d' /etc/inittab &&\
# can't set hostname since docker sets it
    sed -i 's/hostname $opts/# hostname $opts/g' /etc/init.d/hostname &&\
# can't mount tmpfs since not privileged
    sed -i 's/mount -t tmpfs/# mount -t tmpfs/g' /lib/rc/sh/init.sh &&\
# can't do cgroups
    sed -i 's/cgroup_add_service /# cgroup_add_service /g' /lib/rc/sh/openrc-run.sh &&\
# clean apk cache
    rm -rf /var/cache/apk/*

