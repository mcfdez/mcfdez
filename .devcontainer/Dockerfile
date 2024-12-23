# Usa una imagen base ligera basada en Debian
FROM debian:bullseye-slim

# Variables para definir UID y GID del usuario
ARG USER_ID=1000
ARG GROUP_ID=1000

# Instala herramientas necesarias y limpia caché
RUN apt-get update && apt-get install -y --no-install-recommends \
    bash \
    git \
    nano \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Crea el directorio sudoers.d si no existe
RUN mkdir -p /etc/sudoers.d

# Crea un usuario no raíz y configura su entorno
RUN groupadd -g $GROUP_ID vscode \
    && useradd -m -u $USER_ID -g $GROUP_ID vscode \
    && mkdir -p /home/vscode/.ssh /workspace \
    && chown -R vscode:vscode /home/vscode /workspace \
    && echo "vscode ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/vscode

# Configura el directorio de trabajo
WORKDIR /workspace/mcfdez

# Cambia al usuario no raíz
USER vscode

# Configura Bash como shell por defecto
CMD ["bash"]