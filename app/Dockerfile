FROM centos:7
MAINTAINER adrian.lehmann@logmein.com
WORKDIR /atp
COPY build_context/MicrosoftDefenderATPOnboardingLinuxServer.py . #(0)
RUN yum-config-manager --add-repo=https://packages.microsoft.com/config/centos/7/prod.repo
RUN curl https://packages.microsoft.com/keys/microsoft.asc > microsoft.asc
RUN rpm --import microsoft.asc

# Install ATP
RUN yum install -y mdatp python sudo # (1)
RUN python MicrosoftDefenderATPOnboardingLinuxServer.py
# Add mdatp to path
RUN ln -s /opt/microsoft/mdatp/sbin/wdavdaemon /usr/bin/mdatp #(2)
# Validate ATP install by testing org id is not empty and a sample scan works
ENTRYPOINT /bin/sh # (3)
