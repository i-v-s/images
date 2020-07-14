FROM debian:9

RUN apt update -y && apt install -y python3 openssh-server && mkdir /run/sshd && \
    rmdir /home && mkdir /root/.ssh && ssh-keygen -t ed25519 -f /root/key -q -N "" && \
    cat /root/key.pub > /root/.ssh/authorized_keys && \
    echo 'root:test' | chpasswd && \
    sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
# SSH login fix. Otherwise user is kicked off after login
    sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"

RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22/tcp

CMD mkdir -p $CI_PROJECT_DIR/temp/debian9/root && \
    cp /root/key $CI_PROJECT_DIR/temp/debian9/root && \
    ln -s $CI_PROJECT_DIR/temp/debian9/home /home && \
    chmod -R 0777 $CI_PROJECT_DIR/temp/debian9 && \
    /usr/sbin/sshd -D
