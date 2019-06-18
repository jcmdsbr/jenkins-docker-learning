
FROM jenkins/jenkins:latest

USER root

# Install Docker CLI
RUN apt-get update && apt-get install -y apt-transport-https ca-certificates
RUN apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
RUN echo "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce --allow-unauthenticated
RUN apt-get update && apt-get install -y openjdk-8-jre curl git jq

# Get docker-compose in the agent container
RUN curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

# Add user jenkins to docker group (?)
RUN usermod -a -G docker jenkins

# Initialize default configurations
RUN /usr/local/bin/install-plugins.sh git mstest matrix-auth workflow-aggregator docker-workflow blueocean credentials-binding

ENV JENKINS_USER admin
ENV JENKINS_PASS admin

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

VOLUME /var/jenkins_home

USER jenkins