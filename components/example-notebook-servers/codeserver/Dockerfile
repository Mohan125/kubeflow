#
# NOTE: Use the Makefiles to build this image correctly.
#

ARG BASE_IMG=<base>
FROM $BASE_IMG

ARG TARGETARCH

# args - software versions
# https://github.com/coder/code-server/releases
ARG CODESERVER_VERSION=4.96.4

USER root

# install - code-server
RUN curl -fsSL "https://github.com/coder/code-server/releases/download/v${CODESERVER_VERSION}/code-server_${CODESERVER_VERSION}_${TARGETARCH}.deb" -o /tmp/code-server.deb \
 && dpkg -i /tmp/code-server.deb \
 && rm -f /tmp/code-server.deb

# s6 - copy scripts
COPY --chown=${NB_USER}:${NB_GID} --chmod=755 s6/ /etc

USER $NB_UID

EXPOSE 8888