# k8s-deployments-Commands

- Exec into the pod
```
kubectl exec -it frontend-client-6456b9d84-5vp2m  -n frontend -c frontend-client -- /bin/sh
```

- Make a Get Call by service name. This returns response
```
wget -O- http://backend-server.backend/get
```

-  Make a Get Call by service name. This returns Status Code
```
wget -O- http://backend-server.backend/status/:code
```

# Helm-Commands

- Install helm charts
```
helm install frontend ./service -f ./service/values-frontend-app.yaml
```

- Upgrade helm charts
```
helm upgrade --install frontend ./service -f ./service/values-frontend-app.yaml
```

- Render the YAML output
```
helm template frontend ./service -f ./service/values-frontend-app.yaml
```

- DRY RUN Installation
```
helm install frontend ./service -f ./service/values-frontend-app.yaml --dry-run --debug
```