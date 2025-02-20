# java-hello-world-config

## Requisitos

- DockerHub
- GCP ou AWS ou Azure ou Minikube
- Nome de domínio
- [MiniKube](https://minikube.sigs.k8s.io/docs/)

## Deploy

```bash
kubectl apply -f k8s-manifests/
```

## Observações importantes

1. Substitua `seu-usuario/sua-imagem:tag` pela referência correta da sua imagem no DockerHub
2. Gere o secret do DockerHub com:
```bash
kubectl create secret docker-registry dockerhub-secret \
  --docker-server=https://index.docker.io/v1/ \
  --docker-username=seu-usuario \
  --docker-password=sua-senha \
  --docker-email=seu-email \
  -n java-app
```
3. Ajuste os recursos (CPU/memória) de acordo com as necessidades da sua aplicação
4. Configure o domínio correto no Ingress e Certificate
5. Se necessário, crie um IP estático no GCP e configure-o no Ingress
6. Ajuste as configurações do HPA conforme sua necessidade


Estes manifestos fornecem uma base sólida para deploy da aplicação com:

- Alta disponibilidade (múltiplas réplicas)
- Autoscaling baseado em CPU
- HTTPS com certificado gerenciado
- Health checks
- Gerenciamento de configuração via ConfigMap
- Segurança para pull de imagens privadas