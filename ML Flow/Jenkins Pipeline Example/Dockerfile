FROM nexus-gss.uscis.dhs.gov:1337/argos/ironbank/opensource/python/python38:latest as base
ARG HTTP_PROXY=http://preproxy.uscis.dhs.gov:80
ARG HTTPS_PROXY=$HTTP_PROXY
ARG VAULT_NAMESPACE="VIS_nonprod"

ENV HTTP_PROXY=$HTTP_PROXY
ENV HTTPS_PROXY=$HTTP_PROXY
ENV http_proxy=$HTTP_PROXY
ENV https_proxy=$HTTP_PROXY
ENV NO_PROXY="127.0.0.1,169.254.170.2,localhost,.docker,.uscis.dhs.gov"
ENV no_proxy="127.0.0.1,169.254.170.2,localhost,.docker,.uscis.dhs.gov"

ENV VAULT_NAMESPACE=$VAULT_NAMESPACE

USER root
RUN yum install -y openssl && \
    yum install -y libyaml-devel && \
    yum install -y gcc && \
    useradd -ms /bin/bash worker && \
    cd /home/worker && \
    python -m pip --no-cache-dir install --proxy ${HTTPS_PROXY} --force-reinstall -I pyyaml && \
    python -m pip install --proxy ${HTTPS_PROXY} --upgrade pip wheel && \
    python -m pip install --proxy ${HTTPS_PROXY} mlflow==1.19.0 psycopg2-binary boto3 

EXPOSE 5000

ENTRYPOINT ["sh", "-c", "mlflow server --host 0.0.0.0 --backend-store-uri ${DATABASE_URI} --default-artifact-root ${S3_ARTIFACT_URI}"]
