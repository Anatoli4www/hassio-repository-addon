ARG BUILD_FROM=ghcr.io/hassio-addons/base:16.2.1
FROM ${BUILD_FROM}

# Add env
ENV LANG C.UTF-8

# Setup base
RUN \
    apk add --no-cache \
    coreutils=9.5-r1 \
    wget=1.24.5-r0 \
    samba \
    && mkdir -p /var/lib/samba \
    && touch \
        /etc/samba/lmhosts \
        /var/lib/samba/account_policy.tdb \
        /var/lib/samba/registry.tdb \
        /var/lib/samba/winbindd_idmap.tdb

# Copy data
COPY rootfs /

HEALTHCHECK \
    CMD smbclient -L '\\localhost' -U '%' -m SMB3
