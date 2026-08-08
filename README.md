# To-Do
- Install envoy gateway 
```
helm install envoy-gateway oci://docker.io/envoyproxy/gateway-helm --version v1.8.3 -n envoy-gateway-system --create-namespace
```

- Install envoy proxy 
```
kubectl apply -f ./gateway-class/alb-custom-proxy-config.yaml
```

- Use this image for service
```
https://hub.docker.com/r/nginxdemos/nginx-hello
```

# k8s-deployments-Commands

- Exec into the pod
```
kubectl exec -it frontend-client-6456b9d84-5vp2m  -n frontend -c frontend-app -- /bin/sh
```

- Make a Get Call by service name. This returns response
```
wget -O- http://backend-app.backend/get
```

-  Make a Get Call by service name. This returns Status Code
```
wget -O- http://backend-app.backend/status/:code
```

# Helm-Commands

- Install/Upgrade helm charts
```
helm upgrade --install frontend ./service -f ./service/values-frontend-app.yaml
helm upgrade --install backend ./service -f ./service/values-backend-app.yaml
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