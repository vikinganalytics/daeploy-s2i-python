# daeploy/s2i-python
FROM python:3.8-slim

LABEL maintainer="Viking Analytics AB"

ENV BUILDER_VERSION=1.0 \
    APP_ROOT="/opt/app-root" \
    HOME="/opt/app-root/src" \
    STI_SCRIPTS_PATH="/usr/libexec/s2i"

# Set labels used in OpenShift to describe the builder image
LABEL io.k8s.description="Platform for building lightweight Daeploy images" \
    io.k8s.display-name="Daeploy python builder" \
    io.openshift.expose-services="8080:http" \
    io.openshift.tags="builder,daeploy,python." \
    io.openshift.s2i.scripts-url="image://${STI_SCRIPTS_PATH}"

# Setup virtualenv
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Copy the S2I scripts to the image
COPY ./s2i/bin/ $STI_SCRIPTS_PATH

# Set the default port for applications built using this image
EXPOSE 8080

# Setup file system
RUN mkdir -p ${APP_ROOT} && \
    mkdir -p ${HOME}

WORKDIR $HOME

# Set the default CMD for the image
CMD ["$STI_SCRIPTS_PATH/usage"]
