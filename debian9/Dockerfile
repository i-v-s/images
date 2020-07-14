FROM debian:9

RUN apt update -y && apt install -y python3 openssh-server && mkdir /run/sshd && \
    rmdir /home && mkdir /root/.ssh

EXPOSE 22/tcp

CMD echo $TEST_SSH_PUB_KEY > /root/.ssh/authorized_keys && \
    ln -s $CI_PROJECT_DIR/temp/host_test/home /home && \
    /usr/sbin/sshd -D
