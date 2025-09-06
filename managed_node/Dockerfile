FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y python3 openssh-server nginx curl && \
    mkdir /var/run/sshd && \
    echo 'root:root' | chpasswd && \
    sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    service ssh start

COPY ssh_key.pub /root/.ssh/authorized_keys

RUN chmod 600 /root/.ssh/authorized_keys

EXPOSE 22 80

CMD ["/usr/sbin/sshd", "-D"]
