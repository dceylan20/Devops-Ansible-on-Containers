FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y python3 python3-pip openssh-client ansible

COPY inventory /etc/ansible/hosts
COPY playbook.yml /root/playbook.yml
COPY ansible.cfg /etc/ansible/ansible.cfg

RUN mkdir -p /root/.ssh

COPY ssh_key /root/.ssh/id_rsa
COPY ssh_key.pub /root/.ssh/id_rsa.pub

RUN chmod 600 /root/.ssh/id_rsa && \
    chmod 644 /root/.ssh/id_rsa.pub

ENV ANSIBLE_HOST_KEY_CHECKING=False

CMD ["sh", "-c", "ansible-playbook /root/playbook.yml && tail -f /dev/null"]
