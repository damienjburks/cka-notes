# Deployments

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14295508#overview)

## Notes

- Deployments provide the capability to upgrade replica sets seamlessly. They are Kubernetes objects that offer "declarative" updates to Pods and ReplicaSets.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
    name: myapp-deployment
    labels:
        app: myapp
        type: front-end
spec:
    replicas: 3
    template:
        metadata:
            labels:
                app: myapp
                type: front-end
        spec:
            containers:
            - name: nginx-container
                image: nginx
```

- Commands for creating and verifying deployments:

```bash
kubectl create -f deployment-definition.yml
kubectl get deployments
```

- To see all objects at once:

```bash
kubectl get all
```

## Additional Commands

Bookmark this page for the exam: [Kubernetes Kubectl Conventions](https://kubernetes.io/docs/reference/kubectl/conventions/)

- Create an NGINX Pod:

```bash
kubectl run nginx --image=nginx
```

- Generate POD Manifest YAML file without creating it:

```bash
kubectl run nginx --image=nginx --dry-run=client -o yaml
```

- Create a deployment:

```bash
kubectl create deployment --image=nginx nginx
```

- Generate Deployment YAML file without creating it:

```bash
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml
```

- Generate Deployment YAML file and save it to a file:

```bash
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml
```

- Make necessary changes to the file (e.g., adding more replicas) and then create the deployment:

```bash
kubectl create -f nginx-deployment.yaml
```

- Alternatively, in Kubernetes version 1.19+, specify the `--replicas` option to create a deployment with 4 replicas:

```bash
kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml
```
