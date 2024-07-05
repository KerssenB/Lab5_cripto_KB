FROM ubuntu:20.10

RUN sed -i 's/archive.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    sed -i 's/security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    apt-get update && apt-get upgrade

RUN apt-get install tcpdump -y

RUN apt-get install -y build-essential wget zlib1g-dev libssl-dev

COPY ./openssh-8.3p1.tar.gz .

RUN tar zxvf openssh-8.3p1.tar.gz

RUN sed -i '3s/8.3/?/' /openssh-8.3p1/version.h
WORKDIR /openssh-8.3p1
    
RUN ./configure && \
    make && \
    make install

CMD ["tail", "-f", "/dev/null"]

