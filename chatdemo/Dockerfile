# Use minimal Alpine base image
FROM alpine:latest

# Install basic utilities (optional)
RUN apk add --no-cache bash coreutils

# Set working directory (optional)
WORKDIR /mnt/shared

# Keep container running
CMD ["sh", "-c", "while true; do sleep 30; done"]
