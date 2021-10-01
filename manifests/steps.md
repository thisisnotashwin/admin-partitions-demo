** Create a license secret: **
```bash
kubectl create secret generic license --from-literal=key=FOO....BAR //(this is the literal license value)
```

** Copy certificate secrets: **
```bash
kubectl get secret servers-consul-ca-cert --context servers -o yaml | kubectl apply --context red -f -
kubectl get secret servers-consul-ca-key --context servers -o yaml | kubectl apply --context red -f -
```
replace the `servers-consul-ca-cert` and `servers-consul-ca-key` with the name of the secret in your installation on the servers cluster.

replace `servers`, `red` and `blue` with the name of the contexts of your clusters.

The name of the contexts can be found using:
```
kubectl config get-contexts
```