FROM registry.access.redhat.com/ubi9/python-312:latest

COPY ca.crt /tmp

USER 0
# Install any dependencies
RUN \
  cp -v /tmp/ca.crt /etc/pki/ca-trust/source/anchors/  && \
  update-ca-trust && \
  curl http://cli-server.trusted-artifact-signer.svc.cluster.local:8080/clients/linux/cosign-amd64.gz | gunzip | dd of=/usr/local/bin/cosign && \
  curl http://cli-server.trusted-artifact-signer.svc.cluster.local:8080/clients/linux/gitsign-amd64.gz | gunzip | dd of=/usr/local/bin/gitsign && \
  chmod -v +x /usr/local/bin/*

USER 1001
