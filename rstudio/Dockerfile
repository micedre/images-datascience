ARG BASE_IMAGE=inseefrlab/onyxia-r-datascience
FROM $BASE_IMAGE

SHELL ["/bin/bash", "-c"]

ENV DEFAULT_USER=${USERNAME}
ENV USERID=${UID}
ENV GROUPID=${GID}

ENV PATH="/usr/lib/rstudio-server/bin:$PATH"

ARG RSTUDIO_CONF_FILE="/etc/rstudio/rsession.conf"

USER root 

# Install Rstudio using rocker's install scripts
RUN /rocker_scripts/install_rstudio.sh && \
    /rocker_scripts/install_pandoc.sh && \
    # Set default working directory for R sessions and R projects
    echo "session-default-working-dir=${WORKSPACE_DIR}" >> ${RSTUDIO_CONF_FILE} && \
    echo "session-default-new-project-dir=${WORKSPACE_DIR}" >> ${RSTUDIO_CONF_FILE} && \
    # Fix permissions
    chown -R ${USERNAME}:${GROUPNAME} ${HOME} && \
    # Clean
    rm -rf /var/lib/apt/lists/*

EXPOSE 8787

CMD ["/init"]
