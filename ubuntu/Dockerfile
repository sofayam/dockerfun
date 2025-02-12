FROM ubuntu:latest

# Install SSH server and other utilities
RUN apt-get update && \
    apt-get install -y openssh-server sudo && \
    mkdir /var/run/sshd && \
    mkdir /root/.ssh

# Create a user with sudo privileges
RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 ubuntu && \
    echo 'ubuntu:ubuntu' | chpasswd

# Configure SSH
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# Expose SSH port
EXPOSE 22 

# Create directory for persistent data
RUN mkdir /data

# Start SSH service
CMD ["/usr/sbin/sshd", "-D"]