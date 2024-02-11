FROM jenkins/jenkins:latest



# install Maven
USER root
RUN apt-get update
RUN apt-get install -y maven
RUN apt-get install -y wget && rm -rf /var/lib/apt/lists/*
RUN curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 && \
    chmod +x get_helm.sh && \
    ./get_helm.sh
USER jenkins

