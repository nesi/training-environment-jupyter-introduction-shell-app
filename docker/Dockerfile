FROM ubuntu:22.04

# run unminimise
RUN yes | unminimize

# install system dependencies
# TODO: move ldap-utils, libnss-ldapd, libpam-ldapd, nscd, nslcd to base image??
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
        bioawk \
        curl \
        git \
        ldap-utils \
        libnss-ldapd \
        libpam-ldapd \
        less \
        locales \
        man-db \
        nano \
        nodejs \
        nscd \
        nslcd \
        python-is-python3 \
        python3 \
        python3-pip \
        rsync \
        unzip \
        vim \
        wget \
        zip \
    && rm -rf /var/lib/apt/lists/* \
    && localedef -i en_NZ -c -f UTF-8 -A /usr/share/locale/locale.alias en_NZ.UTF-8

ENV LANG en_NZ.utf8

# download the required data into the container image and make sure permission are ok
RUN wget -nv https://github.com/GenomicsAotearoa/introduction-to-shell/releases/download/2024-July/shell_data.zip \
        -O /var/lib/shell_data.zip \
    && unzip /var/lib/shell_data.zip -d /var/lib \
    && rm -f /var/lib/shell_data.zip \
    && chown -R root:root /var/lib/shell_data \
    && chmod -R o+rX /var/lib/shell_data 

# Following data is for inidigitdata intro2shell: download the required data into the container image and make sure permission are ok
RUN wget -nv https://github.com/GenomicsAotearoa/IndigiDataAotearoa-IntroToShell/releases/download/2023-Aug/sample-data.zip \
        -O /var/lib/sample-data.zip \
    && unzip /var/lib/sample-data.zip -d /var/lib \
    && rm -f /var/lib/sample-data.zip \
    && chown -R root:root /var/lib/sample-data \
    && chmod -R o+rX /var/lib/sample-data 


# install jupyterlab
RUN pip3 --no-cache-dir install jupyterlab
