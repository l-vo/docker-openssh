FROM debian:jessie

# Ssh installation and configuration
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin no/' /etc/ssh/sshd_config

# Build args
ARG SSH_USER
ARG SSH_PASSWORD
ARG SSH_VOLUME_DIR

# Add user
RUN echo "${SSH_USER}:${SSH_PASSWORD}:1001:1001::/home/${SSH_USER}:/bin/bash" | newusers
RUN cp /etc/skel/.profile /home/${SSH_USER}
RUN cp /etc/skel/.bashrc /home/${SSH_USER}

EXPOSE 22

# -e allows to have connexion logs
CMD ["/usr/sbin/sshd", "-De"]
