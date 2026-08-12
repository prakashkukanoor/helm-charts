# Install Envoy gateway and application
- Install all below from single command
```
aws eks update-kubeconfig --region us-east-1 --name purchase-eks1-33-dev --profile dev && \
helm install envoy-gateway oci://docker.io/envoyproxy/gateway-helm --version v1.8.3 -n envoy-gateway-system --create-namespace && \
helm upgrade --install envoy-gateway-api ./envoy-gateway-api/ -f ./envoy-gateway-api/dev/values.yaml && \
helm upgrade --install frontend ./application -f ./application/values-frontend-app.yaml && \
helm upgrade --install backendend ./application -f ./application/values-backend-app.yaml

```

- Install envoy gateway 
```
helm install envoy-gateway oci://docker.io/envoyproxy/gateway-helm --version v1.8.3 -n envoy-gateway-system --create-namespace
```

- Install envoy gateway proxy & Route 
```
helm upgrade --install envoy-gateway-api ./envoy-gateway-api/ -f ./envoy-gateway-api/dev/values.yaml
```

- Install frontend & backend application 
```
helm upgrade --install frontend ./application -f ./application/values-frontend-app.yaml
helm upgrade --install backendend ./application -f ./application/values-backend-app.yaml
```

# Helm-Commands

- Create new helm chart or template
```
helm create <chart-name>
```

- Install Uninstall
```
helm uninstall frontend backend
```

- Render the YAML output
```
helm template frontend ./service -f ./service/values-frontend-app.yaml
```

- DRY RUN Installation
```
helm install frontend ./service -f ./service/values-frontend-app.yaml --dry-run="client" --debug
```