# K8s Ollama

## Setup

```bash
kubectl create ns ollama

export PRELOAD_MODEL=( "ollama3.1", "codellama" )
```

create dirs for PV

```sh
mkdir -p /data/k8s/openwebui
mkdir -p /data/k8s/ollama
```

create temp certifactes

```bash
openssl req -newkey rsa:2048 -new -nodes -x509 -days 365 -subj "/CN=example.com" -addext "subjectAltName = DNS:ollama.service,DNS:webui.service" -keyout ollama.key -out ollama.crt
```

create secrets

```shs
kubectl create secret tls ollama -n ollama --cert ollama.crt --key ollama.key
```

create basic-auth

```sh
# install htpasswd if it doesn't exist
#apt install -y apache2-utils

$ htpasswd -c auth ollama
New password:
Re-type new password:
Adding password for user ollama

$ kubectl create secret generic basic-auth --from-file=auth -n ollama
```

Ollama API: <https://github.com/ollama/olama/blob/main/docs/api.md>
