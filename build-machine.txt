FROM jenkins/jenkins:lts
USER root
RUN apt-get update -qq \
    && apt-get install -qqy apt-transport-https ca-certificates curl gnupg2 software-properties-common \
    && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
    && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" \
    && apt-get update  -qq \
    && apt-get install docker-ce=17.09.0~ce-0~debian -y
RUN usermod -aG docker jenkins
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && mv kubectl /bin && chmod +x /bin/kubectl
RUN apt-get install -y git
