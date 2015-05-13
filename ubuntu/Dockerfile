FROM ubuntu:14.04

RUN apt-get update
RUN apt-get install -y gcc autoconf automake libtool flex bison gperf gawk m4 make libssl-dev libreadline-dev git
RUN apt-get clean


WORKDIR /usr/local/src
RUN git clone https://github.com/openlink/virtuoso-opensource.git

WORKDIR /usr/local/src/virtuoso-opensource
RUN git checkout stable/7
RUN ./autogen.sh
RUN CFLAGS="-O2 -m64"
RUN export CFLAGS
RUN ./configure --prefix=/usr/local/ --with-readline=/usr/lib/libreadline.so
RUN make
RUN make install

EXPOSE 8890

WORKDIR /usr/local/var/lib/virtuoso/db/
CMD virtuoso-t -df
