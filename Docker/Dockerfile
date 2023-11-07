FROM debian:stretch-slim

# Install GNOME
RUN apt-get update && apt-get install -y gnome-desktop-environment gnome-terminal

# Install noVNC
RUN apt-get install -y novnc

# Create a user for VNC login
RUN adduser -D -r -s /bin/bash vnc

# Install tigervnc viewer
RUN curl https://dl.bintray.com/tigervnc/stable/tigervnc-1.9.0.x86_64.tar.gz | tar xmzf -C /home/vnc/
RUN cp -R /home/vnc/tigervnc-1.9.0.x86_64/* /

# Configure noVNC
COPY novnc-config.json /home/vnc/
RUN mkdir -p /home/vnc/.config/novnc
COPY novnc-index.html /home/vnc/.config/novnc/index.html

# Start noVNC server
CMD ["/usr/local/bin/noVNC", "-listen", "6080", "-web", "-path", "/home/vnc/index.html"]

# Expose port 6080 for noVNC access
EXPOSE 6080
