FROM quay.io/deis/lightweight-docker-go:v0.2.0
FROM debian:stretch
COPY --from=0 /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt

COPY . /cnab/app
RUN mv /cnab/app/cnab/app/* /cnab/app && rm -r /cnab/app/cnab
RUN apt-get update && \
apt-get install -y apt-transport-https curl && \
curl -o kubectl https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kubectl && \
mv kubectl /usr/local/bin && \
chmod a+x /usr/local/bin/kubectl

RUN apt-get update && \
 apt-get install -y curl && \
 curl -o helm.tgz https://storage.googleapis.com/kubernetes-helm/helm-v2.12.3-linux-amd64.tar.gz && \
 tar -xzf helm.tgz && \
 mv linux-amd64/helm /usr/local/bin && \
 rm helm.tgz
RUN helm init --client-only
# exec mixin has no buildtime dependencies

WORKDIR /cnab/app
CMD ["/cnab/app/run"]