FROM quay.io/openshift/origin-jenkins-agent-base:4.2

LABEL com.redhat.component="jenkins-agent-helm-ubi7-docker" \
      name="openshift/origin-jenkins-agent-helm-ubi7" \
      version="4.2" \
      architecture="x86_64" \
      release="1" \
      io.k8s.display-name="Jenkins Agent Helm" \
      io.k8s.description="The jenkins agent helm image has helm on top of the jenkins agent base image." \
      io.openshift.tags="openshift,jenkins,agent,helm"

ENV HELM_VERSION=3.0.3
ENV BASE_URL="https://get.helm.sh"
ENV TAR_FILE="helm-v${HELM_VERSION}-linux-amd64.tar.gz"

ADD ubi.repo /etc/yum.repos.d/ubi.repo

RUN curl -L ${BASE_URL}/${TAR_FILE} |tar xvz && \
    mv linux-amd64/helm /usr/bin/helm && \
    chmod +x /usr/bin/helm && \
    rm -rf linux-amd64

USER 1001

ENTRYPOINT ["helm"]
CMD ["--help"]
