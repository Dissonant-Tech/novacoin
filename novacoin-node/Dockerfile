FROM ubuntu:latest

RUN apt-get update -y
RUN apt-get install -y build-essential libtool \
    autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils \
    software-properties-common python-software-properties git

RUN add-apt-repository ppa:bitcoin/bitcoin && apt-get update -y

RUN apt-get install -y libboost-all-dev libdb4.8-dev libdb4.8++-dev

RUN git clone https://github.com/innovacoin/innova.git /usr/src/app

WORKDIR /usr/src/app

RUN ./autogen.sh && ./configure
RUN make && make install

COPY innova.conf /root/home/innovacore/innova.conf

CMD ["innovad"]
