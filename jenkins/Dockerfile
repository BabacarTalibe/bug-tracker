FROM jenkins/jenkins:lts-jdk21

USER root

# Installer lsb-release
RUN apt-get update && apt-get install -y lsb-release curl wget tar

# Installer Docker CLI
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
    https://download.docker.com/linux/debian/gpg

RUN echo "deb [arch=$(dpkg --print-architecture) \
    signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
    https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list

RUN apt-get update && apt-get install -y docker-ce-cli

# Installer Go
RUN wget https://go.dev/dl/go1.22.5.linux-amd64.tar.gz \
    && tar -C /usr/local -xzf go1.22.5.linux-amd64.tar.gz \
    && rm go1.22.5.linux-amd64.tar.gz

# Ajouter Go au PATH
ENV PATH=$PATH:/usr/local/go/bin

USER jenkins
