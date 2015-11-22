FROM debian:8

RUN apt-get update
RUN apt-get -fy install build-essential
RUN apt-get -fy install libtool-bin
RUN apt-get -fy install libgtk-3-dev
RUN apt-get -fy install libgconf2-dev
RUN apt-get -fy install libsqlite3-dev
RUN apt-get -fy install liblensfun-dev
RUN apt-get -fy install libgphoto2-dev
RUN apt-get -fy install libexiv2-dev
RUN apt-get -fy install libfftw3-dev
RUN apt-get -fy install git
RUN apt-get -fy install autoconf
RUN apt-get -fy install automake
RUN apt-get -fy install libjpeg-dev
RUN apt-get -fy install libtiff-dev
RUN apt-get -fy install apt-utils
RUN apt-get -fy install libxml2-dev
RUN apt-get -fy install liblcms2-dev
RUN apt-get -fy install enfuse

# Build
RUN git clone --depth 1 https://github.com/rawstudio/rawstudio /rawstudio

WORKDIR /rawstudio
RUN ./autogen.sh
RUN make
RUN make install
RUN ldconfig

# Configure user
ENV UID=1000
ENV GID=1000

RUN mkdir /home/user
RUN groupadd user -g $UID
RUN useradd user -d /home/user -u $UID -g $GID -s /bin/bash
RUN chown -R user:user /home/user

VOLUME /data
USER user

ENTRYPOINT /usr/local/bin/rawstudio
