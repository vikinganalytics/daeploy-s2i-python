# daeploy/s2i-python
FROM python:3.7-slim

LABEL maintainer="Viking Analytics AB"

ENV BUILDER_VERSION=1.0 \
    APP_ROOT="/app_root" \
    STI_SCRIPTS_PATH="/.s2i/bin"

# Set labels used in OpenShift to describe the builder image
LABEL io.k8s.description="Platform for building Daeploy images with reduced size" \
    io.k8s.display-name="Daeploy python builder" \
    io.openshift.expose-services="8080:http" \
    io.openshift.tags="builder,daeploy,python." \
    io.openshift.s2i.scripts-url="image://.s2i/bin"

# Setup virtualenv
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Copy the S2I scripts to the image
COPY ./s2i/bin/ .s2i/bin

# TODO: Set the default port for applications built using this image
EXPOSE 8080

# TODO: Set the default CMD for the image
CMD [".s2i/bin/usage"]
