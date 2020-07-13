FROM debian:9

RUN apt update -y && apt install -y python3 openssh-server && mkdir /run/sshd && \
    mkdir -p /builds/temp/host_test/root && mkdir /root/.ssh && \
    ln -s /builds/temp/host_test/root/authorized_keys /root/.ssh/authorized_keys && \
    rmdir /home && ln -s /builds/temp/host_test/home /home

EXPOSE 22/tcp

CMD [ "/usr/sbin/sshd", "-D" ]
