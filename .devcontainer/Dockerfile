FROM debian:bullseye-slim

# Install Git and other basic utilities
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY . .

CMD ["tail", "-f", "/dev/null"]