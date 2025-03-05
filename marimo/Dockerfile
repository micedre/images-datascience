ARG BASE_IMAGE=inseefrlab/onyxia-python-datascience
FROM $BASE_IMAGE

LABEL maintainer="InseeFrLab <innovation@insee.fr>"

USER root

ARG marimo_version=0.8.15

ENV MARIMO_SKIP_UPDATE_CHECK=1

RUN pip install --no-cache-dir marimo==${marimo_version} && \
  mkdir -p /app/data && \
  chown -R ${USERNAME}:${GROUPNAME}  ${HOME} && \
  pip install --no-cache-dir marimo[sql]

USER 1000

EXPOSE 8888

ENV HOST=0.0.0.0

CMD ["marimo", "edit", "--no-token",  "-p $PORT",  "--host $HOST"]
