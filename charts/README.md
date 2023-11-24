## Usage

install helm

```bash
# refer: https://github.com/helm/helm/releases

export INST_HELM_VERSION=v3.13.2

cd $(mktemp -d) \
&& curl -sL "https://get.helm.sh/helm-${INST_HELM_VERSION}-linux-${INST_HELM_ARCH}.tar.gz" -o ./helm-linux.tar.gz \
&& tar zxvf ./helm-linux.tar.gz -C . \
&& mv ./linux-${INST_HELM_ARCH}/helm /usr/local/bin/helm-${INST_HELM_VERSION} \
&& chmod +x /usr/local/bin/helm-${INST_HELM_VERSION} \
&& update-alternatives --install /usr/bin/helm helm /usr/local/bin/helm-${INST_HELM_VERSION} 1 \
&& alternatives --set helm /usr/local/bin/helm-${INST_HELM_VERSION} 

```

install this charts as a library chart, add to ` Chart.yaml `

```bash
dependencies:
  - name: chart-common
    repository: oci://
    version: 1.x.x
```

upgrade dependency

```bash
helm dependency update
```
