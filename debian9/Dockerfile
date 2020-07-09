FROM debian:9

RUN apt update && apt install -y python3 openssh-server && mkdir /run/sshd

CMD [ "/usr/sbin/sshd", "-D" ]
