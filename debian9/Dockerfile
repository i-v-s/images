FROM debian:9

RUN apt update -y && apt install -y python3 openssh-server && mkdir /run/sshd && \
    rmdir /home && mkdir /root/.ssh && ssh-keygen -t ed25519 -f /root/key -q -N "" && \
    cat /root/key.pub > /root/.ssh/authorized_keys

EXPOSE 22/tcp

CMD mkdir -p $CI_PROJECT_DIR/temp/debian9/root && \
    cp /root/key $CI_PROJECT_DIR/temp/debian9/root && \
    ln -s $CI_PROJECT_DIR/temp/debian9/home /home && \
    chmod -R 0777 $CI_PROJECT_DIR/temp/debian9 && \
    /usr/sbin/sshd -D
