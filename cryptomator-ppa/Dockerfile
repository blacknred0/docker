FROM ubuntu:xenial
MAINTAINER sebastian.stenzel@cryptomator.org

ENV LANG=C.UTF-8

# Install Build Dependencies
RUN apt-get update \
	&& apt-get -y --no-install-recommends install curl ca-certificates debhelper devscripts build-essential fakeroot dput \
	&& apt-get clean

# import gpg key
COPY A8240A09.asc /tmp/
RUN gpg --import /tmp/A8240A09.asc

# initialize build directory
COPY build.sh /var/build/
COPY debian /var/build/debian/

ENV CRYPTOMATOR_VERSION=1.2.1 \
  CRYPTOMATOR_FULL_VERSION=1.2.1-0ppa1 \
  GPG_PASSPHRASE=toBeSpecifiedWhenRunningThisContainer

# create debian source package
CMD cd /var/build \
  && bash /var/build/build.sh
