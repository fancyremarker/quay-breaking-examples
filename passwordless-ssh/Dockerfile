FROM quay.io/aptible/ubuntu:12.04

# Install sshd
RUN apt-get update
RUN apt-get -y install openssh-server && \
    mkdir -p /var/run/sshd && chmod go+rx /var/run/sshd
ADD templates/ssh /etc/ssh

# Add passwordless git user
RUN adduser --disabled-password --gecos "Git" git && passwd -d git

RUN rsyslogd && /usr/sbin/sshd && ssh -o StrictHostKeyChecking=no git@localhost
RUN cat /var/log/auth.log
