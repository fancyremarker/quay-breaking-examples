FROM quay.io/aptible/ubuntu:12.04

# Install sshd
RUN apt-get update
RUN apt-get -y install openssh-server && \
    mkdir -p /var/run/sshd && chmod go+rx /var/run/sshd
ADD templates/ssh /etc/ssh
ADD templates/bin/test-shell /usr/bin/test-shell

# Add passwordless git user
RUN adduser --disabled-password --gecos "Git" \
      --shell /usr/bin/test-shell git && passwd -d git

RUN rsyslogd && /usr/sbin/sshd && \
    ssh -o StrictHostKeyChecking=no git@localhost || true
RUN cat /var/log/auth.log
