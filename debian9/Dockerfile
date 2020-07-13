FROM debian:9

RUN apt update -y && apt install -y python3 openssh-server && mkdir /run/sshd && \
    mkdir -p /builds/temp/host_test/root && mkdir /root/.ssh && \
    ln -s /root/.ssh/authorized_keys /builds/temp/host_test/root/authorized_keys && \
    rmdir /home && ln -s /home /builds/temp/host_test/home

EXPOSE 22/tcp

CMD [ "/usr/sbin/sshd", "-D" ]
