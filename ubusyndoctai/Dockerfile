# First create a Dockerfile
FROM ubuntu:latest

# Install required packages
RUN apt-get update && \
    apt-get install -y curl gnupg && \
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/jammy.gpg | apt-key add - && \
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/jammy.list | tee /etc/apt/sources.list.d/tailscale.list && \
    apt-get update && \
    apt-get install -y tailscale && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Create startup script
RUN echo '#!/bin/bash\n\
tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/var/run/tailscale/tailscaled.sock &\n\
sleep 5\n\
tailscale up --authkey=$TAILSCALE_AUTHKEY --hostname=$HOSTNAME\n\
# Keep container running\n\
tail -f /dev/null' > /start.sh && \
    chmod +x /start.sh

CMD ["/start.sh"]
