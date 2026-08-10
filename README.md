# Install Envoy gateway and application
- Install frontend application 
```
helm upgrade --install frontend ./app-service -f ./app-service/values-frontend-app.yaml
helm upgrade --install backend ./app-service -f ./app-service/values-backend-app.yaml
```

- Install envoy gateway 
```
helm install envoy-gateway oci://docker.io/envoyproxy/gateway-helm --version v1.8.3 -n envoy-gateway-system --create-namespace
```

- Install envoy gateway proxy & Route 
```
kubectl apply -R -f ./envoy-gateway-api/
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
helm install frontend ./service -f ./service/values-frontend-app.yaml --dry-run --debug
```