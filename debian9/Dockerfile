FROM debian:9

RUN apt update -y && apt install -y python3 openssh-server && mkdir /run/sshd && \
    mkdir /root/.ssh && rmdir /home 

EXPOSE 22/tcp

ENTRYPOINT ln -s $CI_PROJECT_DIR/temp/host_test/root/authorized_keys /root/.ssh/authorized_keys && \
           ln -s $CI_PROJECT_DIR/temp/host_test/home /home

CMD [ "/usr/sbin/sshd", "-D" ]
