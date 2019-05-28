FROM centos

RUN yum -y install openssh-server

RUN useradd centos_user && \
    echo "matrix" | passwd centos_user --stdin && \
    mkdir /home/centos_user/.ssh && \
    chmod 700 /home/centos_user/.ssh

COPY remote_centos_key.pub /home/centos_user/.ssh/authorized_keys

RUN chown centos_user:centos_user -R /home/centos_user/.ssh/ && \
    chmod 600 /home/centos_user/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen

CMD /usr/sbin/sshd -D