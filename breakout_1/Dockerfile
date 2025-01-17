FROM ubuntu:18.04
COPY main.c  /opt/
WORKDIR /opt/
RUN apt-get update -y; apt-get install openssh-server gcc gdbserver tmux -y && gcc /opt/main.c -o /opt/flag;
COPY ./config/passwd /etc/passwd
COPY ./config/shadow /etc/shadow
COPY ./config/sshd_config /etc/ssh/sshd_config
COPY ./config/start.sh /tmp/
EXPOSE 8080
ENTRYPOINT ["/tmp/start.sh"]
