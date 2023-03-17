FROM  mcr.microsoft.com/devcontainers/base:jammy

RUN apt-get update \
    && apt-get install --no-install-recommends -y rsyslog systemd systemd-cron \
    # Fix a bug with common-debian script
    && rm -f /usr/local/bin/systemctl \
    #  Clean up
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        dmsetup \
        libseccomp-dev \
        automake \
        lvm2 \
        inotify-tools \
        entr \
        udev \
    && rm -rf /var/lib/apt/lists/*

CMD ["/lib/systemd/systemd", "--system", "--unit=basic.target"]