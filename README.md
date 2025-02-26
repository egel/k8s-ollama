# K8s Ollama

```bash
kubectl create ns ollama

export PRELOAD_MODEL=( "ollama3.1", "codellama" )
```


create temp certifactes

```bash
openssl req -newkey rsa:2048 -new -nodes -x509 -days 365 -subj "/CN=example.com" -addext "subjectAltName = DNS:ollama.service,DNS:webui.service" -keyout ollama.key -out ollama.crt
```


Ollama API: <https://github.com/ollama/ollama/blob/main/docs/api.md>
