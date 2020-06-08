FROM jenkins/jenkins:lts

USER root

ENV BASE_APKS="sudo openssl openssh-client zip ttf-dejavu maven ruby" \
    BUILD_APKS=" make gcc clang g++ paxctl binutils-gold autoconf bison" \
    JAVA_OPTS="-Djenkins.install.runSetupWizard=false" \
    CASC_JENKINS_CONFIG="/var/jenkins_home/jenkins.yaml"

RUN apt-get update && apt-get install -y $BASE_APKS $BUILD_APKS && rm -rf /var/lib/apt/lists/*

# Add Node in here later

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

COPY jenkins.yaml /var/jenkins_home/jenkins.yaml
RUN chown jenkins:jenkins /var/jenkins_home/jenkins.yaml
USER jenkins
