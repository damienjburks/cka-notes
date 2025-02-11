# Daemon Sets

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14295586#content)

[Lab Link](https://uklabs.kodekloud.com/topic/practice-test-daemonsets-2/)

## Notes

- Helps you deploy multiple instances of a pod and replicates a pod across all nodes.
    - Ensures that one copy of the pod is present on all nodes in the cluster.
- Use Cases: monitoring agent or log viewer (e.g., Grafana and Prometheus).
- `kube-proxy` is required on each node and can be deployed in a daemon set.

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
    name: my-daemonset
    labels:
        app: my-app
spec:
    selector:
        matchLabels:
            app: my-app
    template:
        metadata:
            labels:
                app: my-app
        spec:
            containers:
            - name: my-container
                image: my-image:latest
                ports:
                - containerPort: 80
```
- Almost exactly like the ReplicaSet definition file.

```bash
kubectl create -f daemonset.yaml
```
- From v1.12, daemonsets use node affinity and the default scheduler.