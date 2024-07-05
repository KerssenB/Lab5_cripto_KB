FROM ubuntu:22.10

RUN sed -i 's/archive.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    sed -i 's/security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    apt-get update && apt-get install -y openssh-client openssh-server

RUN apt-get install tcpdump -y && apt-get update

## Para el paso 3
COPY ./sshd_config /etc/ssh/sshd_config

RUN useradd -m -p $(openssl passwd -1 prueba) prueba
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

CMD ["/usr/sbin/sshd", "-D", "-e"]

